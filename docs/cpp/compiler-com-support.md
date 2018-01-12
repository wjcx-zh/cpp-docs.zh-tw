---
title: "編譯器 COM 支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b05fdff690f8693e926011c3bc7d1738ee9be66c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-com-support"></a>編譯器 COM 支援
## <a name="microsoft-specific"></a>Microsoft 特定的  
 Visual C++ 編譯器可直接讀取元件物件模型 (COM) 類型程式庫，以及內容轉譯成可在編譯時包含的 C++ 原始程式碼。 語言擴充功能可協助您進行用戶端的 COM 程式設計。  
  
 使用[#import 前置處理器指示詞](../preprocessor/hash-import-directive-cpp.md)，編譯器可以讀取類型程式庫，並轉換到 c + + 標頭檔描述 COM 介面標記為類別。 一組 `#import` 屬性可供使用者控制產生類別程式庫標頭檔的內容。  
  
 您可以使用[__declspec](../cpp/declspec.md)擴充的屬性[uuid](../cpp/uuid-cpp.md)来指派給 COM 物件的全域唯一識別碼 (GUID)。 關鍵字[__uuidof](../cpp/uuidof-operator.md)可以用來擷取與 COM 物件相關聯的 GUID。 另一個`__declspec`屬性[屬性](../cpp/property-cpp.md)，可以用來指定**取得**和**設定**COM 物件的資料成員的方法。  
  
 一組 COM 支援全域函式和類別提供來支援**VARIANT**和`BSTR`類型，實作智慧型指標，以及封裝所擲回的錯誤物件`_com_raise_error`:  
  
-   [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)  
  
-   [_bstr_t](../cpp/bstr-t-class.md)  
  
-   [_com_error](../cpp/com-error-class.md)  
  
-   [_com_ptr_t](../cpp/com-ptr-t-class.md)  
  
-   [_variant_t](../cpp/variant-t-class.md)  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)   
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)