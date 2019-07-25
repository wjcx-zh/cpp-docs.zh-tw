---
title: 輸入輸出資料流程
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: 3d5344ede3a62375c4c8102d1fc39445518eb0c4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455264"
---
# <a name="inputoutput-streams"></a>輸入/輸出資料流

在標頭檔 \<istream> 中定義的 `basic_iostream` 是處理輸入和輸出字元型 I/O 資料流之物件的類別範本。

有兩個 typedef 可定義 `basic_iostream` 的字元特定特製化，並協助讓程式碼變得更容易讀取：`iostream` (請勿與標頭檔 \<iostream> 混淆) 是一個以 `basic_iostream<char>` 為基礎的 I/O 資料流；`wiostream` 是一個以 `basic_iostream<wchar_t>` 為基礎的 I/O 資料流。

如需詳細資訊，請參閱 [basic_iostream 類別](../standard-library/basic-iostream-class.md)、[iostream](../standard-library/basic-iostream-class.md) 及 [wiostream](../standard-library/basic-iostream-class.md)。

衍生自 `basic_iostream` 的是類別範本 `basic_fstream`，此範本可用來將字元資料串流處理至檔案，或從檔案串流處理字元資料。

此外，也有提供 `basic_fstream` 之字元特定特製化的 typedef。 它們是 `wfstream`, 這是以 char 為基礎的檔案 i/o 資料流程, 而則是以 wchar_t 為基礎的檔案 i/o 資料流程。  `fstream` 如需詳細資訊，請參閱 [basic_fstream 類別](../standard-library/basic-fstream-class.md)、[fstream](../standard-library/basic-fstream-class.md) 及 [wfstream](../standard-library/basic-fstream-class.md)。 使用這些 typedef 時，必須包含標頭檔 \<fstream>。

> [!NOTE]
> 當使用 `basic_fstream` 物件來執行檔案 I/O 時，雖然基礎緩衝區包含個別指定的讀取和寫入位置，但目前的輸入和輸出位置是繫結在一起的，因此讀取某些資料時會移動輸出位置。

類別範本 `basic_stringstream` 及其常見的客製化 `stringstream` 經常用來與 I/O 資料流物件搭配運作，以插入和擷取字元資料。 如需詳細資訊，請參閱 [basic_stringstream 類別](../standard-library/basic-stringstream-class.md)。

## <a name="see-also"></a>另請參閱

[stringstream](../standard-library/basic-stringstream-class.md)\
[basic_stringstream 類別](../standard-library/basic-stringstream-class.md)\
[\<sstream>](../standard-library/sstream.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
