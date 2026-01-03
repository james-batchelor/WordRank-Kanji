# WordRank Kanji

An anki kanji deck - [Ankiweb link](https://ankiweb.net/shared/info/1766033327)

(This is a personal project which I've wrapped up into a minimal repo, for in case anybody wants to regenerate the deck with their own corpora or weightings. It's not intended to be a library / module, the notebook is the build pipeline. Steps to recreate the deck: prepare txt files in data/ as rows of Japanese sentences, pip install -r requirements.txt, then run the notebook top down. Further optional steps (i.e. audio generation) are explained in the notebook markdown.)

## The problem

I wanted to learn kanji, and learn vocabulary too along the way. So I tried a few resources, but they'd often choose and omit words for each kanji in opaque and (I gradually realised) sometimes strange ways. And then also, when you're looking at a set of words and their translations, you pick which ones to remember based on the usefulness / commonality in English, but that doesn't really capture how natural and common those words actually are in Japanese. So with these two things in effect I felt like I was learning a lot of unhelpful Japanese.

As an example, when learning 定 I was shown 定める meaning "to fix" among other things, and I thought that was useful to remember. So then one evening I pointed to a wonky wardrobe door in my apartment and said 定めたい to a native Japanese person, who had no idea what I was trying to say, because it a) it really means to fix/decide a decision e.g. in a legal contract, and b) it's kind of literary and official language, not very common in everyday Japanese. "Not common Japanese" was a phrase I was starting to hear more and more as I was going through the deck. And I ended up getting more and more frustrated, that I was putting a lot of effort into learning vocabulary when it felt like a minefield of weird and uncommon language, and I had no way to know which were the mines.

## The solution

There are many decks which give kanji and vocabulary in a rough frequency order, but I didn't see any which give a vocabulary breakdown for each kanji in its own proportional frequency ranking. So, I made a deck which does that: WordRank Kanji.

## WordRank Kanji Features

- Cards are sorted by kanji frequency: You learn kanji which unlock the most vocabulary first. (But some kanji are still grouped by theme, e.g. weather, body parts, ..., and there is a starter set for the very beginning.)
- Vocabulary are also frequency sorted: For each kanji, the words are ordered by how often the kanji appears in each word. 予定/指定/設定 all beat 定まる because 定 appears in each of the others more often.
- 5k / 10k / >10k vocab markers: The shading of the frequency proportion / percent value tells you how common the word is globally.
- Audio recordings for words: tap each word for a tts-generated recording. (The speech model isn't perfect, so if the recording doesn't match the written pitch accent, trust what's written.)
- Pitch accent highlighting (Tokyo style): Orange mora for atamadaka, red for nakadaka, purple for odaka, and green for heiban (to distinguish from when the deck doesn't have pitch accent data for the word). If you'd like to learn more then I'd recommend [kanshudo](www.kanshudo.com/howto/pitch). You can toggle this on or off by going to Manage note types > WordRank Kanji > css, then change between 1 and 0 as it describes.
- Stroke order: you can toggle on a stroke order font for card backs in the same way.
- Katakana reading training: You can also toggle for using katakana in furigana.
- Built using 24M sentences from diverse linguistic sources: Spoken (movie / TV / anime subtitles, lecture transcripts) and written (internet crawl / social media, literature, wikipedia) sources are both used for balanced learning -- although I skew towards spoken.
- Buttons linking to Wanikani / Kanji Damage / Kanji Koohi / Jisho: Quick access to mnemonics and references. You can add / remove websites by editing the card back html also.
- Cards are JLPT level / Jōyō grade tagged: You can filter cards to these tags if that aligns with your goals. The deck includes all Jōyō and JLPT kanji, all in the top 2.5k of pure frequency ranking, and some rarer but useful ones (e.g. sushi menu items).

![image showing example cards with features annotated](https://i.postimg.cc/ry9M2r12/annotated-cards.png)

### Notes on Usage

The card backs have a lot of vocabulary, but it's up to you to decide which ones you'll hold yourself to learning. So don't be overwhelmed, it's not sensible to try learn 15 words for every kanji from the start. You'll find that you'll pick up many of those words anyway when you get to the less common kanji in each pair -- 当該 isn't the most common word for 当, but it is for 該.

The main thing the deck doesn't have are example sentences. I think it would just be too information-dense for flash card study with everything else it has, and I prefer graded readers for reading practise personally.

### Extra Things

If you prefer a different order for the cards than pure frequency then it's very easy to reorder the deck. You need to prepare a csv file with two columns, one with just each kanji on its own, and the second column the new rank. Then import that csv to anki, merge on the kanji column, and use your ranking column to overwrite the "Deck Order (overwrite this one)" field, which I've left as a placeholder for this purpose. Now that the ordering data is in the deck, go to the card browser (B), sort the cards by the field, ctrl+A, right click and reposition. (If you've already reviewed some cards, then also filter to "is:new" before the ctrl+A.)

Also, some vocab breakdowns don't sum to 100%, because words are only added if definitions and kana readings exist for them in the dictionaries. So really obscure words, hanzi hybrids, or (what's usually the case) most nouns in the corpora are dropped.

And finally, I hope you find the deck useful! :)

![image showing the kanji included in the deck as a plot of frequency against jlpt / jouyou level](https://i.postimg.cc/ZKLnnKWM/inclusions.png)