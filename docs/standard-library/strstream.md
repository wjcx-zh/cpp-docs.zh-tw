---
title: '&lt;strstream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<strstream>
- std::<strstream>
- <strstream>
dev_langs:
- C++
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 665d71e2c5966dd04cd72d7b2ad24c9f32fde206
ms.lasthandoff: 02/24/2017

---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;
定義可為已配置的 `char` 物件陣列所儲存之序列的 iostreams 作業提供支援的數個類別。 這類序列會輕易地與 C 字串相互轉換。  
  
## <a name="syntax"></a>語法  
  
```  
#include <strstream>  
  
```  
  
## <a name="remarks"></a>備註  
 類型 `strstream` 的物件可與 `char` * (是 C 字串) 搭配運作。 使用 [\<sstream>](../standard-library/sstream.md)，來與類型 [basic_string](../standard-library/basic-string-class.md) 的物件搭配運作。  
  
> [!NOTE]
>  `<strstream>` 中的類別已被取代。 請考慮改用 `<sstream>` 中的類別。  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[strstreambuf 類別](../standard-library/strstreambuf-class.md)|此類別說明一個資料流緩衝區，它可控制元素與 `char` 陣列物件中儲存的元素序列之間的相互傳輸。|  
|[istrstream 類別](../standard-library/istrstream-class.md)|此類別說明一個物件，該物件可控制如何從類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中擷取項目和編碼物件。|  
|[ostrstream 類別](../standard-library/ostrstream-class.md)|此類別說明一個物件，該物件可控制如何在類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中插入項目和編碼物件。|  
|[strstream 類別](../standard-library/strstream-class.md)|此類別說明一個物件，該物件可控制如何使用類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區來插入及擷取項目和編碼物件。|  
  
## <a name="see-also"></a>另請參閱  
 [\<strstream>](../standard-library/strstream.md)   
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)




