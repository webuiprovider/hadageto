+++
title = "Duplication vs Replication"
description = "Copying a document makes it another document"
date = "2020-04-14T12:00:00+00:00"
draft = false
categories = ["tech", "business"]
tags = ["why","background","replication", "copying", "duplication"]
slug = "duplication-vs-replication"
images = []
+++

Let's take a common scenario. You're a small business, and you get a lawyer to draft a contract, which you then send to a customer.

Your lawyer attaches the document in PDF format to an email, and sends it to you. You save a copy on your hard drive for your records, and create a new email to your customer which you attach the contract to. So far, so absolutely normal for a business transaction.

{{<img src="/signing.jpg" title="Normal business transactions involve communication of documents" caption="" alt="image of a business transaction in progress with two people signing a document">}}

The thing is, there are now 7 copies of that document:

1. The "original" on your lawyer's hard drive
2. The copy on their email server attached to the email they sent
3. The copy on your email server attached to the email you received
4. The copy on your hard drive
5. The second copy on your email server attached to the email you sent to your customer
6. The copy on your customer's email server attached to the email they received
7. The copy on your customer's hard drive

And in fact, we're being slightly generous here. Given everyone's use of email on phones and tablets, there are probably a few more copies kicking around. And that doesn't include any backups taken.

Each of these copies could be different, and there would be no way of telling. A malicious employee (for example) could change the contents of the document and no-one would be any the wiser until the court case. Someone could change the version sitting on the email server, and you'd never know. 

During the discovery process of the court case, this whole trail would be unwound and each copy inspected to determine what changed, and where. There would be legal arguments about which version is the "real" document. If any changes took place, is the "real" document the changed one, or the original one?

## Will the real document please stand up?

{{<img src="/paperwork-piles.png" title="If every transaction involves at least 7 copies, how many copies are there?" caption="and which one is the legally-admissable one?" alt="image of a businessperson overwhelmed with copies of documents">}}

Part of the problem here is that there is no definitive "single source of truth" in this exchange. The lawyer provided the original, but it's actually the version that you send your customer that's the important one. But is that the one attached to the email you sent, or the one attached to the email they received? There's no way of telling.

Hadageto has a solution for this, rooted firmly in Document Management best practice: Hadageto's document storage is read-only. You cannot change a document once uploaded. No-one can. This is a huge difference from most online document "collaboration" services, which allow documents to be edited online.

The reason for this is that Hadageto is designed to be the "single source of truth" for your documents. Once you have uploaded a document, it remains as it was when uploaded. 

If we revisit the business transaction, but use Hadageto, it looks like this:

1. Your lawyer creates a new draft contract for you, and uploads it to your Hadageto account via the upload link you send them.
2. You download the document from Hadageto so you can review it.
3. You send a download link to your customer so they can download the document direct from your Hadageto store.

There are less copies in this transaction; 4 instead of 7:

1. A copy on the lawyer's hard drive that was then uploaded
2. A copy on your hard drive that you reviewed
3. A copy on the customer's hard drive that they downloaded
4. An encrypted, read-only copy on the Hadageto file store

But the main difference is that in this process there is only one "true" copy - the copy on Hadageto's store. The document that your customer downloads is not a copy of a copy of a copy of a copy of the document that your lawyer wrote. It's verifiably a first-generation copy of the document that your lawyer uploaded.

That "verifiably" is important. We can prove that the document sent to your customer via that download link is a true copy of the document sent by your lawyer, and we can prove that in court. The document on Hadageto is always the "true" version of the document.

## Duplication isn't Replication

In some cases, though, multiple people will want a copy of the same document for their own files. In the example above, either your lawyer or your customer may also use Hadageto and want "their" copy to be single source of truth. Normally, you'd both have separate copies of the document, stored on separate hard drives (and backup drives) and again there would be no way of telling which one was the "true" one.

Hadageto solves this by "replication". Instead of duplicating the document into each account, creating multiple copies and potential conflict, Hadageto allows you to "replicate" the document. What that means is that the document gets added to both accounts. The same, single source of truth now exists in both accounts.

Should you and your lawyer part ways, you both keep the same document, shared between you. Should you decide that you don't need that document any more, then you can remove it from your account. It still remains on your ex-lawyer's account. There aren't multiple copies of the document, it's just the one copy, owned by and available to multiple people.

If your customer downloads the document, and later decides to join Hadageto, and then uploads that document to their account, it's not the same document. Because the customer downloaded it, it disappeared from the audit trail, and so the system treats it as another, different document. It will be given a new ID number, and tracked as a completely new document. This is the safest way to be sure that the document wasn't changed while it wasn't being audited.

{{<img src="/inbox_outbox.jpg" title="Duplication leads to many copies, replication leads to a single shared copy" caption="" alt="image of a business person sat between two piles of documents">}}

This way you can send people links to your documents, or share your documents with them, knowing that your originals are safe and that you can always prove that your copy is the "true" one. Someone may download the document you sent them, but that doesn't mean they now own that document. They own a copy of the document, which isn't the same thing at all. They can do anything to that copy, and there's no way of proving they didn't. They can't touch the true copy on Hadageto.

Should there be a dispute later, and you end up in court trying to prove that the document you sent had the vital clause in it, then Hadageto can help. The download link will be on the audit trail, with the document ID. The document ID points to the exact document that was uploaded originally. There's no way it can be altered, and so the document downloaded must be the same as the document uploaded. There's no confusion, and no way for anyone to credibly claim that their version of the document is the "real" one.

## Versions and Signatures

We are working on two features that are relevant here.

Versions will let you upload a different version of the same document. This effectively allows you to modify the document in an audited manner. Each version of the document is retained, and is unchangeable. Any upload or download links point at a specific version, so it is always possible to determine specifically which version was sent or received via a link. The versions of a document are numbered, so the history of modifications can be reviewed. And the latest version is the one that the system returns for most operations.

Signatures will allow a Hadageto member to digitally sign a document. The signature will be secure, in that the only way it can be generated is by the person who owns that signature. The process of signing will generate a new "signed" version of the document, optionally with a watermark or some visual indicator of having been signed.

Let us know what you think of these features, whether they'd be important for your business.

## Conclusion

Anyone can download a document from an email, change it, and claim that that was the version they received. People try this all the time, it's a common type of fraud. Sending documents by email generates legal complications because every step of the email chain generates duplicate documents. 

Hadageto solves this problem by preserving the integrity of the document and auditing any actions on it. It remains the trusted "single source of truth" for your business documents. And we can prove it.