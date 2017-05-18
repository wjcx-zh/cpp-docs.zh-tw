---
title: "輸入/輸出資料流 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 4fdfb4ece713c071a4b740127428c16303c0ab10
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="inputoutput-streams"></a>輸入/輸出資料流
在標頭檔 \<istream> 中定義的 `basic_iostream` 是處理輸入和輸出字元型 I/O 資料流之物件的類別範本。  
  
 有兩個 typedef 可定義 `basic_iostream` 的字元特定特製化，並協助讓程式碼變得更容易讀取：`iostream` (請勿與標頭檔 \<iostream> 混淆) 是一個以 `basic_iostream<char>` 為基礎的 I/O 資料流；`wiostream` 是一個以 `basic_iostream<wchar_t>` 為基礎的 I/O 資料流。  
  
 如需詳細資訊，請參閱 [basic_iostream 類別](../standard-library/basic-iostream-class.md)、[iostream](../standard-library/basic-iostream-class.md) 及 [wiostream](../standard-library/basic-iostream-class.md)。  
  
 衍生自 `basic_iostream` 的是類別範本 `basic_fstream`，此範本可用來將字元資料串流處理至檔案，或從檔案串流處理字元資料。  
  
 此外，也有提供 `basic_fstream` 之字元特定特製化的 typedef。 這包括 `fstream` (以 `char` 為基礎的 I/O 資料流) 和 `wfstream` (以 `wchar_t` 為基礎的 I/O 資料流)。 如需詳細資訊，請參閱 [basic_fstream 類別](../standard-library/basic-fstream-class.md)、[fstream](../standard-library/basic-fstream-class.md) 及 [wfstream](../standard-library/basic-fstream-class.md)。 使用這些 typedef 時，必須包含標頭檔 \<fstream>。  
  
> [!NOTE]
>  當使用 `basic_fstream` 物件來執行檔案 I/O 時，雖然基礎緩衝區包含個別指定的讀取和寫入位置，但目前的輸入和輸出位置是繫結在一起的，因此讀取某些資料時會移動輸出位置。  
  
 類別範本 `basic_stringstream` 及其常見的客製化 `stringstream` 經常用來與 I/O 資料流物件搭配運作，以插入和擷取字元資料。 如需詳細資訊，請參閱 [basic_stringstream 類別](../standard-library/basic-stringstream-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [stringstream](../standard-library/basic-stringstream-class.md)   
 [basic_stringstream 類別](../standard-library/basic-stringstream-class.md)   
 [\<sstream>](../standard-library/sstream.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)




