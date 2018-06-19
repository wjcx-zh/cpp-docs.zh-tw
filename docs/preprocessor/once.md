---
title: 一旦 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.once
- once_CPP
dev_langs:
- C++
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b0e0b2b3667d4a33709caa643e4d26ed70b2990
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912923"
---
# <a name="once"></a>once
指定編譯原始程式碼檔案時，編譯器只能包含 (開啟) 檔案一次。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma once  
  
```  
  
## <a name="remarks"></a>備註  
 因為編譯器不會在轉譯單元中檔案的第一個 #include 之後開啟及讀取檔案，所以使用 `#pragma once` 可以縮短建置時間。 這指*多個 include 最佳化*。 它有的效果類似於 *#include 防護*慣用語，使用前置處理器巨集定義來防止多次包含檔案的內容。 這也有助於避免違反*一個定義規則*-要求的所有範本、 類型、 函式和物件只能有一個定義您的程式碼中。  
  
 例如:   
  
```  
// header.h  
#pragma once  
// Code placed here is included only once per translation unit  
  
```  
  
 對新程式碼我們建議 `#pragma once` 指示詞，因為它不會干擾全域命名空間與前置處理器符號。 它需要的輸入較少，較不令人分心，而且不會造成符號衝突，不同標頭檔使用相同的前置處理器符號做為防護值時造成的錯誤。 它不是 C++ Standard 的一部分，但它可能由數個常見編譯器實作。  
  
 在同一個檔案中同時使用 #include 防護慣用語和 `#pragma once` 並沒有任何益處。 如果在此慣用語的標準形式之前或之後沒有非註解程式碼或前置處理器指示詞，編譯器會辨識 #include 防護慣用語並以與 `#pragma once` 指示詞的相同方式實作多個 include 最佳化：  
  
```  
// header.h  
// Demonstration of the #include guard idiom.  
// Note that the defined symbol can be arbitrary.  
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_  
#define HEADER_H_  
// Code placed here is included only once per translation unit  
#endif // HEADER_H_  
  
```  
  
 必須將程式碼移植到不會實作 `#pragma once` 指示詞的編譯器或是當多個 include 最佳化不可能時，我們建議採用 #include 防護慣用語，以維護與現有程式碼的一致性。 在檔案系統別名 include 路徑防止編譯器依正式路徑識別相同 include 檔案的複雜專案中，便可能發生此情況。  
  
 請注意，不要在設計目的是要併入多次的標頭檔中使用 `#pragma once` 或 #include 防護慣用語，使用前置處理器符號來控制其效果。 如需這項設計的範例，請參閱\<assert.h > 標頭檔。 也請小心管理 include 路徑，以避免建立多個 include 檔案的路徑，如此可以同時戰勝 #include 防護和 `#pragma once` 的多個 include 最佳化。  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)