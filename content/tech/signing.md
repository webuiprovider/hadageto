+++
title = "Signatures"
description = "How Hadageto handles signatures"
date = "2020-04-07T12:00:00+00:00"
draft = true
categories = ["tech"]
tags = ["why","background","encryption", "security", "signatures", "document management"]
slug = "signatures"
images = []
+++

Signing digital documents is a hard problem. It's hard not because of the technology. It's hard because we humans refuse to accept a flawed digital singing process, when we cheerfully accept a flawed physical signing process.

Let's start with the physical process. If two people want to create a binding agreement between them, they write the agreement out on a piece of paper, twice, and then each of them sign both copies. They both keep one copy. If either of them break the agreement, the other one can produce their signed copy of the document to prove what the agreement was and therefore that it has been broken.

The agreement is only enforceable by a Court of Law. The court (usually the judge) needs to decide if the agreement was valid, if it was broken, and what should happen to make amends for it being broken. So these agreements are written with the court in mind, and the court has procedures and processes for deciding whether such agreements are valid.

The signature part of it needs to prove that both parties agreed to the written agreement. The questions that need to be resolved are:

1. Did this person sign the document? (i.e. is this a forgery of their signature?)
2. Did the person sign this document? (i.e. has the signature been transferred to another document, or did they believe they were signing a different document)

There are also other considerations, like "was the person forced to sign it?", "was the person mentally capable of knowing what they agreed to when they signed it?". But those are out of scope for this discussion.

Physical signatures are not very good at doing either of these things. It is relatively simple to forge a signature. And so common that "forger" is a recognisable criminal profession. And it is relatively simple to include text in a document that the signer won't read. So common that we have a phrase for it: "the fine print".

Because physical signatures have been the only answer for hundreds of years, our legal practices have adapted to this. There are legal processes and shortcuts around dealing with the limitations of the signature process. Such as requiring witnesses (so if one party says the signature was forged, the witness can be summoned to the court to testify that it wasn't).

But when signing digital documents, we refuse to accept any system that doesn't fix both these problems. And then because we refuse to accept any such system, we end up with a compromise of inserting a signature JPG into a PDF file. Which doesn't solve any of these problems, but does have the one advantage that it superficially resembles the physical signing process. Extracting the digital signature from a PDF document is very simple, and then it can be inserted into any other document the forger likes. There is nothing stopping someone from changing the text of a contract, then inserting the other party's signature file into it, and claiming this as the original. The fact that this doesn't happen very often is amazing, and evidence that signatures don't actually matter that much.

It's true. They don't. You can accept the Terms of Use for a website (a binding agreement that can give rise to criminal prosecution if breached) by clicking a box on a web page. You don't need to sign it to make it legally enforceable. There are all sorts of other agreements that are legally binding without ever needing to be signed.

However, in the context of a business contract, for example, it is important that all parties sign the agreement to make it binding. So how do we implement this in Hadageto?

## Deconstruct to Reconstruct

As with all problems of a process being implemented as a computer system, we need to pull it all apart so we can put it back together.

As we saw above, the important bits about the signing process are:

1. The person signing actually performed the signing process. In other words, it can't be forged by someone else.
2. The document being signed is the one that the person signing thinks they're signing. In other words, the document can't be substituted during the signing process, and the resulting signature can't be transferred to another document.

To this we'll add, because we're not dealing with paper and pens any more, these:

1. The document is obviously signed. It should be easy to determine on a casual inspection whether a document is signed or unsigned
2. The document cannot be changed once signed without either becoming unsigned, or leaving obvious traces of alteration.

In addition:

1. A document can be signed either unilaterally, where each person signs it regardless of whether anyone else does, or multilaterally, where the document is not signed until everyone agrees to sign it.
2. Everyone who signed it gets a copy of the signed document, and it can be shared to other people who haven't signed it while retaining its "obviously signed" property.

Putting this together, we need a process where:

1. A document (or collection of documents) can be put through a singing process.
2. A specific set of one or more people are designated as signers in the process, either unilaterally or multilaterally.
3. Each signer does something to indicate that they are signing the document. Whatever this action is, it can be only done by the signer themselves.
4. The document is altered during the process of signing, and that alteration indicates that this document has been signed by all the signers. The unsigned and signed versions of the document must be obviously different.
5. It is possible to determine exactly who signed the document by examining it.
6. It is not possible to recreate the signature(s) without the involvement of the signer themselves.
7. It is not possible to extract the signature from the document and apply it to another document.

There's another couple of technical requirements thrown in:

1. Any cryptography code used must be from a trusted source, and audited by trusted third parties. Cryptography is extremely difficult to get right, so we must be careful when using it to make sure we only use audited code correctly.
2. Wherever possible, the result should be compatible with open standards. It should be possible to verify the signatures using a common external tool rather than relying on Hadageto.

Putting this all back together, we can see that this should be our process:

1. A Hadageto user proposes that one or more people sign a document, either unilaterally or multilaterally. This can just be that one person themselves.
2. An email is sent to all the people involved. The email contains a link to a special "signing" page. The signing page contains the document to be signed, which the signer can download or view in the browser. The signer can review the document for as long as they like.
3. If the signer decides to sign the document, they log in to Hadageto. If they don't have an account, they can create one at this point.
4. If the document is to be signed multilaterally, Hadageto records the signature details for the signer. When all the signatories agree, the system uses the stored details for each signatory. If the document is to be signed unilaterally, it is signed immediately.
5. And here we hit the problem. Signing a document creates a signature, but for most document formats there's no method of including such a signature in the document. PDF, Word and LibreOffice documents use completely different methods for attaching a signature into the document. Most digital signature systems use a "wrapper" file around the document that contains the signature.
6. 




