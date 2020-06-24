+++
title = "Why Not End to End Encryption?"
description = "Explaining why Hadageto doesn’t end-to-end encrypt"
date = "2020-04-07T12:00:00+00:00"
draft = false
categories = ["tech"]
tags = ["why","history","background","e2e","encryption", "security"]
slug = "why-no-e2e"
images = []
+++

There's been a lot of talk about end-to-end encryption recently, in particular in relation to video conferencing products.

We thought we'd explain why Hadageto doesn't use end-to-end encryption in our product.

{{<img src="/padlock_keyboard.jpg" title="Security is important" caption="image courtesy of The Digital Way on Pixabay" alt="an image of a padlock sitting on a laptop computer keyboard">}}

## What is end-to-end encryption?

All data on computers is stored as a series of bytes. Which can also be interpreted as numbers. Any content (such as any of your documents) is effectively a single huge number. 

Encryption is the process of using a **key** (another number) to perform a mathematical operation on the number that represents your content to produce another number. The special part of the process is that it's extremely difficult to get from the resulting number back to the original number without the key. 

The "too long, didn't read" is that encryption needs a key to work. If you have the key, you can decrypt the document. If you don't have the key, you can't.

End-to-end encryption means that the content (in this case, your documents) are encrypted at one end of the communication stream (in this case, when you decide to upload them). They are then decrypted at the other end of the process (when you view them). The content is never decrypted at any point in the process of communicating it, but only at the ends. Hence "end-to-end" encryption.

The important part of end-to-end encryption (and why it is used) is that the servers used to manage the communication of the content cannot read the actual content. They don't have the key, so they can't decrypt the content, and so they can't read it. This has follow-on effects: e.g. a court-issued search warrant for the content will fail because the servers can't read the content.

The security of any encryption system depends on good key management. The data is only as safe as the key (just as in the physical world with physical keys). Key storage and management is extremely important, and very difficult to do securely.

{{<img src="/login_page.jpg" title="Authentication and Encryption work together" caption="image courtesy of mohamed Hassan on Pixabay" alt="a picture of a login page on a tablet computer">}}

## How does Hadageto's encryption work?

Hadageto's encryption works in two stages.

Firstly, the communication between your browser and our server is protected by HTTPS. This is the standard, industry-wide, method of protecting data in motion between browsers and servers. All data between the browser and the server is encrypted, using a key provided by (in this case), [Let's Encrypt](https://letsencrypt.org/)  which provides secure keys for hundreds of millions of websites.

On the server, documents are encrypted using a file key. This key is generated uniquely for each document. The file key is then encrypted using an account key, which is shared between the members of that account. The account key is then encrypted using a personal key, which is further encrypted using your login password.

So when you log in, the server uses your login password to decrypt your personal key, and then uses that to decrypt your account key. It then holds that in memory while you're logged in (and forgets your personal key and password immediately). When you want to view a file, it uses the account key to decrypt the file key, and then uses the file key to decrypt the document, which is then re-encrypted using HTTPS to send to your browser. This is all done in a single "streaming" action, so at no point does the file being sent to your browser exist on the server decrypted.

By the way, your password is never stored on our system. The point of using a personal and account key like this is so that we don't have to store your password, we just need it when you log in. Which we need  anyway to know that you are you.

All of this means that when you upload a document to the server, there is a very small period of time when the document exists as a decrypted file on our servers. And that's the only time the document is ever held as a decrypted file on our system - we don't need to store the file decrypted ever again.

## Why do we do it like this?

There are many reasons, so let's go through them:

### Thumbnails, search and other useful stuff

At the moment, we generate a thumbnail of the document while it's decrypted just after uploading. This helps you find your documents (especially photos) and creates a better experience.

We plan on using machine learning to classify your documents so that we can provide better search. At the moment, search just uses the tags and the document title. We plan on allowing you to search for specific words or phrases in your documents. We can combine all these to give you very precise search for all your documents. We have the goal of providing a Google-like experience for search. You should be able to start typing what you're looking for, and the system will provide the exact document you're looking for by the time you've got three words in. But to do this, we need to know what words your documents have in them.

### Screening for illegal content

If you plan on storing child pornography, or a collection of copyrighted movie files, or details of your upcoming terrorist activity, then please don't use our service. Or do, but be prepared for the consequences.

We comply with legal law enforcement requests to access content stored on our systems. This includes search warrants that are legally presented to us. But it doesn't include "fishing expeditions" through content on our systems looking for evidence. In other words: if the police suspect you of a crime, they can get a search warrant from a judge for documents stored on Hadageto, and we will comply with that warrant and provide them copies of your documents.

There is a debate about end-to-end encryption that we as a society need to have. We agree that it is necessary in some circumstances, but not in all cases. In this particular instance, where our service is intended to store run-of-the-mill business and personal documents, we feel it is better for society if we are able to comply with legal discovery requests.

### Key management is difficult

Creating a protocol where the server can manage your keys without ever being able to know them is difficult, and involves a much more protracted setup and sign-on process. It involves more steps, and more keys, and every one of those is a potential weak point that could be used by an attacker.

We're able to make a more secure process, with less opportunities for bad people to break in, if we don't end-to-end encrypt. We're not denigrating other people's processes - there are brilliant people out there who have created secure end-to-end encryption processes. But we can be more sure that our process is secure if we keep it simple.

Our priority when designing this system is to protect your documents from bad people while allowing you to control who sees them. We can do this better if we manage the keys on the server.

### End-to-end encryption doesn't make you more secure

End-to-end encryption is not designed to protect participants against hackers. It is designed to protect participants against access by the providers of the service itself. To use an analogy: it doesn't make your mail harder to steal; it makes it difficult for the postman to read your mail.

End-to-end encryption is about not trusting the people providing the service. Instead of holding the keys for your encrypted content on the server, the keys are held on your device. The service provider can't access your content because they don't have the keys to decrypt it.

But the trade-off is that the keys are on your device, and need to be protected there. There's lots of ways of doing that, and if someone has your device then you have other, probably bigger, problems. But the trade-off is still there.

Again, our priority is security against bad people accessing your documents. If you think we are one of the bad people, then you probably shouldn't be using our service. If you think the police are bad people, then you probably shouldn't be using our service.

{{<img src="/boxes.jpg" title="keeping strangers from reading your mail" caption="image courtesty of pxfuel.com" alt="an image of a row of locked mailboxes">}}

## Conclusion - this may change

We had to make a choice about end-to-end encryption. We decided to go with not implementing it, for the reasons we've outlined above.

However, that decision is not fixed in stone. We can decide to change our minds and provide end-to-end encryption for either some or all of your documents. As with all decisions about our product, we mostly base our decisions on feedback from our customers.

We will also consider how this access is used by our society. To be blunt; if we receive search warrants or law enforcement requests that we think are trivial, or infringing our customer's privacy too much, then we always have the option of implementing end-to-end encryption and making everyone's lives harder.

If you feel strongly about our decision, please let us know. We're interested in being part of the debate that we as a society need to have about end-to-end encryption.

