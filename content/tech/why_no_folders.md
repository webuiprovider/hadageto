+++
title = "Why Tags Not Folders?"
description = "Explaining why Hadageto doesn’t have folders"
date = "2020-03-30T12:00:00+00:00"
draft = false
categories = ["tech"]
tags = ["why","history","background","tags","no folders"]
slug = "why-no-folders"
images = []
+++

In a nutshell, because our “traditional” folder view is actually very bad at its job.

To understand this, we need some context and history. Early computer systems stored files on a storage medium as a set of files, with no structure. Just a big ol’ list of files. Obviously, this created problems when people wanted to store two files with the same name. And when the number of files got large, with being able to find them.

The solution was to create “directories” - group files together and store them in another file, but in a way that the File System understands and can present as a hierarchical data structure. This is easy for computers to understand, makes file storage easy, and allows operations on whole groups of files with ease. Despite the huge advances in computers and Computer Science over the last 75 years, this directory concept is still the same as it was back then.

{{<img src="/filing_drawer.jpeg" title="The present looks surprisingly like the past" caption="Photo courtesy of Maksym Kaharlytskyi on Unsplash" alt="image of a filing cabinet drawer full of index cards">}}

When Graphical User Interfaces (such as MacOS and Windows) were invented, they mirrored the directory structure into “folders”. Explaining to normal computer users how directories work was a bit difficult, so they used the concept of a conventional paper filing system to explain it. We got used to files living in folders, which lived in drives that used an icon of a filing cabinet to represent it. Everyone understood how this works, because it’s exactly the same as the paper filing system they’re used to.

But, and here’s the important bit: electronic files aren’t paper. Paper files can only be in one place at one time. Electronic files can appear in multiple folders at the same time. We can create “links” in a folder that point to a file in a completely different folder, but that appear to be the actual file. Because the folder is just a metaphor for the underlying directory system, we don’t have to follow it exactly.

And there are lots of problems with a folder system when we’re actually looking for things. Most documents have multiple ways of being filed. An invoice, for instance, has a date, a supplier, and a customer (at least). We could sensibly file the invoice under any of these values. Choosing which one is a fairly major decision that will have ramifications on the organisation forever afterwards. Re-filing all the invoices under date instead of supplier would be a major undertaking.

But for electronic documents, there’s no reason not to file the same document under all three values. Looking in the “supplier invoices” folder, we should see this invoice. And again in the “March 2020” folder, or the “Q1 2020” folder, or the “2020” folder. But this stretches the whole concept of a folder system too far. If documents can be in multiple folders, then what does a folder even mean? And we still have a problem; if we want to create a new folder with some existing documents in it, then we have to go through all the existing documents and add them to the folder.

{{<img src="/hashtag_beach.jpg" title="Tags are cool" caption="Image courtesy of Tanja-Denise Schantz on Pixabay" alt="image of a hashtag symbol written in sand on a beach">}}

Enter Hadageto’s tag system. Instead of putting a document into a folder, we tag the document with the things we want to track about it. So an invoice from Acme for some Roadrunner Traps gets tagged with, say: #invoice #Mar 2020, #Acme, #Roadrunner Project, #unpaid, #authorised. Once tagged, the document then becomes visible in any way we like. If we want to find all the invoices for the Roadrunner project from Q1 2020 that haven’t been paid yet, then we can find them easily by looking at the tags (all documents that have #invoice, #Jan 2020/#Feb 2020/#Mar 2020, #Roadrunner Project and #unpaid). In Hadageto, we can even save this query as a “binder” of documents, that will automatically update itself based on the tags on the relevant documents.

This way, tags can also easily be used for simple workflows. If we paid the Acme invoice, we can remove the #unpaid tag, and possibly add a #paid Mar 2020 tag. We can create a binder of all the documents that are #unpaid from #Feb 2020. We can create a binder of all the invoices that don’t have an #authorised tag yet, so we know with a glance what needs authorisation. Coyote can create a binder of all #Roadrunner project #invoice(s) that don’t have an #authorised tag and authorise them as they appear.

There are plenty of other good things that happen, too. Folders never get too full to be useful. We don’t spend hours trying to remember which folder we put that file in (because it can now be in all the places we think to look for it in).

It takes a bit of getting used to. The temptation is to think of binders as “being like folders”, and to give documents only a couple of tags because then they’ll be in the right binders. But experimenting with adding more tags soon yields results. Everything is easily found. Creating subsets of documents and watch lists is simple. Keeping track of documents that need attention is obvious.

You can even have a “#needs tagging” tag that tells you what documents you need to tag properly. By default, Hadageto adds the “#to be filed” tag to all documents uploaded with no other tags, which you can use for the same purpose.

Social media is increasingly moving to a #tag system for the same reason. Grouping related things together using tags is easy and quick. Finding things using tags is easy and quick. Finding what you want in a vast pool of content is difficult, and tags have become the answer. That answer works as well for documents in your filing system as it does for selfies in your Instagram feed.

It’s time to free ourselves from the limitations of our past. Electronic documents aren’t paper documents. They don’t have the same restrictions. Let’s take advantage of that and use a filing system that works for us instead of constraining us. 

{{<img src="/hashtag_pavement.jpg" title="Tags are the future" caption="image courtesy of Jon Tyson on Unsplash" alt="image of a hashtag on a pavement saying Love One Another">}}



 
