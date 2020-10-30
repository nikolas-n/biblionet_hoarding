# Biblionet
This repo explores the new API of Biblionet and how data can be hoarded from it. Soon I'll add some ways of exploring the data downloaded to do some analysis, stats and whatnot.

To download a book, we can issue a simple curl command as follows:

```
curl -s "https://biblionet.diadrasis.net/wp-json/biblionetwebservice/get_title" -d "username=USER" -d "password=PASSWORD" -d "title=160747" > tmp.json
```

To pretify it, we can use `jq` as follows:

```
cat tmp.json | jq '.' > 160747.json
``` 

Thus, the file we'll end up will contain the following:


```
[
  [
    {
      "TitlesID": "160747",
      "CoverImage": "/wp-content/uploadsTitleImages/17/b160747.jpg",
      "Title": "Ιλιάς",
      "Subtitle": "Ραψωδίες Ν-Ω",
      "ParallelTitle": "",
      "AlternativeTitle": "",
      "OriginalTitle": "",
      "ISBN": "978-960-325-940-4",
      "ISBN_2": "",
      "ISBN_3": "",
      "ISMN": "",
      "Publisher": "Άγρα",
      "WriterName": "Όμηρος",
      "FirstPublishDate": "2010-11-01",
      "CurrentPublishDate": "2010-11-01",
      "FuturePublishDate": null,
      "Place": "Αθήνα",
      "TitleType": "Βιβλίο",
      "EditionNo": null,
      "Cover": "Σκληρό εξώφυλλο",
      "Dimensions": "23x17",
      "PageNo": "329",
      "Availability": "Κυκλοφορεί",
      "Price": "51.0000",
      "VAT": "6",
      "Weight": "754",
      "AgeFrom": null,
      "AgeTo": null,
      "Summary": "Ο Δ.Ν. Μαρωνίτης ολοκληρώνει με τις 12 τελευταίες ραψωδίες από την Ιλιάδα, το μεγάλο έπος του Ομήρου, μετά την ιστορική πλέον μετάφρασή του της \"Οδύσσειας\". Είναι η πρώτη μεγάλη μετάφραση που γίνεται μετά τη μετάφραση Καζαντζάκη-Κακριδή. \r\n\r\nΟ Πρίαμος, γιός του Δαρδάνου, στρέφει το βλέμμα του\r\nΘαυμάζοντας τον Αχιλλέα· ψηλόκορμος κι ωραίος,\r\nμ' έναν θεό του φάνηκε παρόμοιος. Συνάμα ο Αχιλλέας\r\nτον Δαρδανίδη Πρίαμο θαύμαζε κι αυτός, την όμορφή του\r\nόψη, τον τρόπο που μιλούσε.\r\nΌταν, ένας τον άλλον βλέποντας, τον αμοιβαίο θαυμάσμό τους \r\nχόρτασαν, πρώτος τον λόγο πήρε ο Πρίαμος, γερός θεόμορφος. \r\n\r\n\"Η Ιλιάδα είναι έπος πολεμικό: δραματοποιεί, ανατέμνει και συμπυκνώνει τον τρωικό πόλεμο σε τέσσερις μάχιμες ημέρες, που καταλήγουν σε ισόπαλη τραγωδία: ο φόνος του Πάτροκλου από τον Έκτορα και ο φόνος του Έκτορα από τον Αχιλλέα σφραγίζονται με ενδεκαήμερη ανακωχή, αφήνοντας μετέωρο το ερώτημα ποιος είναι ο νικητής και ποιος ο ηττημένος. Τελικώς ο ιλιαδικός πόλεμος περαιώνεται δίχως νικητές και νικημένους. Αντ' αυτού ο αμοιβαίος σπαραγμός (του Αχιλλέα για τον αγαπημένο εταίρο του, του Πριάμου για τον αγαπημένο του γιό) οδηγεί σε ένα είδος συμφιλίωσης των αντιπάλων, υπογραμμίζοντας συνάμα την τραγωδία του πολέμου.\"\r\n",
      "Language": "",
      "LanguageOriginal": "αρχαία ελληνικά",
      "LanguageTranslatedFrom": "αρχαία ελληνικά",
      "Contains": null,
      "Series": null,
      "SeriesNo": null,
      "SubSeries": null,
      "SubSeriesNo": null,
      "MultiVolumeTitle": "Ιλιάς",
      "SetISBN": "960-325-924-1",
      "VolumeNo": "2",
      "VolumeCount": "2",
      "Specifications": null,
      "WebAddress": null,
      "Comments": "Επιλεγόμενα: Δ. Ν. Μαρωνίτης. Η τιμή αφορά συνολικά και τους 2 τόμους."
    }
  ]
]
```

In the torrent of this repo you can find all the book entries of biblionet that had been catalogued until 23th of October 2020.

# Analysis of data
Since the files are in JSON form, we can easily setup an elasticsearch index and visualize/explore data with kibana.

