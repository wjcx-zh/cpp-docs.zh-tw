---
title: 輸入輸出資料流程
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: 54b53f96d487e466106fe92a01affa7bd3e55c16
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228254"
---
# <a name="inputoutput-streams"></a>輸入/輸出資料流

`basic_iostream`（定義于標頭檔中 \<istream> ）是處理輸入和輸出字元型 i/o 資料流程之物件的類別樣板。

有兩個 typedef 會定義的字元特定特製化 `basic_iostream` ，並有助於讓程式碼更容易閱讀： `iostream` （不會與標頭檔混淆 \<iostream> ）是以為基礎的 i/o 資料流程 `basic_iostream<char>` ; 是以為基礎的 i/o `wiostream` 資料流程 `basic_iostream<wchar_t>` 。

如需詳細資訊，請參閱 [basic_iostream 類別](../standard-library/basic-iostream-class.md)、[iostream](../standard-library/basic-iostream-class.md) 及 [wiostream](../standard-library/basic-iostream-class.md)。

衍生自 `basic_iostream` 的是類別範本 `basic_fstream`，此範本可用來將字元資料串流處理至檔案，或從檔案串流處理字元資料。

此外，也有提供 `basic_fstream` 之字元特定特製化的 typedef。 它們是 `fstream` ，這是以為基礎的檔案 i/o 資料流程 **`char`** ，而則是以 `wfstream` 為基礎的檔案 i/o 資料流程 **`wchar_t`** 。 如需詳細資訊，請參閱 [basic_fstream 類別](../standard-library/basic-fstream-class.md)、[fstream](../standard-library/basic-fstream-class.md) 及 [wfstream](../standard-library/basic-fstream-class.md)。 使用這些 typedef 需要包含標頭檔 \<fstream> 。

> [!NOTE]
> 當使用 `basic_fstream` 物件來執行檔案 I/O 時，雖然基礎緩衝區包含個別指定的讀取和寫入位置，但目前的輸入和輸出位置是繫結在一起的，因此讀取某些資料時會移動輸出位置。

類別範本 `basic_stringstream` 及其常見的客製化 `stringstream` 經常用來與 I/O 資料流物件搭配運作，以插入和擷取字元資料。 如需詳細資訊，請參閱 [basic_stringstream 類別](../standard-library/basic-stringstream-class.md)。

## <a name="see-also"></a>另請參閱

[stringstream](../standard-library/basic-stringstream-class.md)\
[basic_stringstream 類別](../standard-library/basic-stringstream-class.md)\
[\<sstream>](../standard-library/sstream.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)
