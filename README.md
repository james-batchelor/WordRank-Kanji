# WordRank Kanji

(This is a personal project which I've wrapped up into a minimal repo, for in case anybody wants to regenerate the deck with their own corpora or weightings. It's not intended to be a library/module, the notebook is the build pipeline. Steps to recreate the deck: prepare txt files in data/ as rows of Japanese sentences, pip install -r requirements.txt, then run the notebook top down. Further optional steps (i.e. audio generation) are explained in the notebook markdown.)


## The problem

I wanted to learn kanji, and learn vocabulary too along the way. So I tried a few resources, but they always seemed to choose and omit words for each kanji in opaque and (as I gradually realised) sometimes strange ways. And then also, when you're looking at a set of words and their translations, you pick which ones to remember based on the usefulness/commonality in English, but that doesn't really capture how natural and common those words actually are in Japanese. So with these two things in effect I felt like I was learning a lot of unhelpful Japanese.

As an example, when learning 定 I was shown 定める meaning "to fix" among other things, and I thought that was useful to remember. So then one evening I pointed to a wonky wardrobe door in my apartment and said 定めたい to a native Japanese person, who had no idea what I was trying to say, because it a) it really means to fix/decide a decision e.g. in a legal contract, and b) it's kind of literary and official language, not very common in everyday Japanese. "Not common Japanese" was a phrase I was starting to hear more and more as I was going through the deck. And I ended up getting more and more frustrated, that I was putting a lot of effort into learning vocabulary when it felt like a minefield of weird and uncommon language, and I had no way to know which were the mines.


## The solution

There are many decks which give kanji and vocabulary in a rough frequency order, but I didn't see any which give the vocabulary breakdown for a kanji in it's own proportional frequency ranking. So I ended up making a deck which does that: WordRank Kanji.

## WordRank Kanji Features

- Cards are sorted by kanji frequency: You learn kanji which unlock the most vocabulary first (although some kanji are still grouped by theme, e.g. weather, body parts, ...).
- Words are also frequency sorted: For each kanji, the vocabulary are ordered by how often the kanji appears in each word. 予定/指定/設定 all beat 定まる because 定 appears in each of the others more often.
- 5k/10k/10k+ vocab markers: The shading of the frequency proportion/% value tells you how common the word is globally.
- Pitch accent highlighting: Orange mora for atamadaka, red for nakadaka, purple for odaka, and green for heiban (to distinguish from when the deck doesn't have pitch accent data for the word).
- Audio recordings for words: tap each word for a tts-generated recording. (The speech model isn't perfect, so if the recording doesn't match the pitch accent shown then trust the pitch accent.)
- Stroke order: you can toggle on a stroke order font for card backs (go to Manage note types > WordRank Kanji > css, and then change between 0 and 1 as it describes).
- Katakana reading training: You can also toggle for using katakana in furigana.
- Built using 24M sentences from diverse linguistic sources: Spoken (movie/anime subtitles, lecture transcripts) and written (literature, wikipedia) sources are both used for balanced learning, although I skew towards spoken. See the repo for details, if you'd like to adjust weights or add your own corpora.
- Buttons linking to Wanikani / Kanji Damage / Kanji Koohi / Jisho: Quick access to mnemonics and references.
- Cards are JLPT level / Jōyō grade tagged: You can filter cards to these tags if that aligns with your goals. The deck includes all Jōyō and JLPT kanji, all in the top 2.5k of pure frequency ranking, and some rarer but useful ones (e.g. sushi menu items).

### Notes on Usage

The card backs have a lot of vocabulary but it's up to you to decide which ones you'll hold yourself to learning. So don't be overwhelmed, it's not viable to try learn 15 words for every kanji from the start. But you'll also find that you'll pick up many of those words anyway when you get to the less common kanji in each pair. 当該 isn't the most common word for 当 but it is for 該.

The main thing the deck doesn't have are example sentences, because I think it would just be too information-dense for flash card study with everything else it has, and I prefer graded readers for real reading practise.

### Extra Things

If you prefer a different order for the cards than pure frequency then it's very easy to reorder the deck. You just need to prepare a csv file with two columns, one with just each kanji on its own, and the second column the new rank. Then import that csv to anki, merge on the kanji column, and use your ranking column to overwrite the "Deck Order (overwrite this one)" field which I've left as a placeholder for this purpose. Now that the ordering data is in the deck, go to the card browser (B), sort the cards by the field, ctrl+A, right click and reposition. (If you've already reviewed some cards, then also filter to "is:new" before the ctrl+A.)

Also some vocab breakdowns don't sum to 100% as vocab rows are only added if definitions and kana readings are available in dictionaries. So really obscure words, hanzi hybrids, or (what's usually the case) most nouns in the corpora are dropped. I think it's more misleading than helpful to recalculate percents after this. It only starts to get really noticeable pretty deep into the deck though.