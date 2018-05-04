---
title: 編譯器 COM 支援類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4fe4e7c26d1b32f16d524407279e5e71534d00c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-com-support-classes"></a>編譯器 COM 支援類別
**Microsoft 特定的**  
  
 標準類別用來支援某些 COM 類型。 類別定義於\<comdef.h > 和產生類型程式庫的標頭檔。  
  
|類別|用途|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|包裝 `BSTR` 類型可提供有用的運算子和方法。|  
|[_com_error](../cpp/com-error-class.md)|定義所擲回的錯誤物件[_com_raise_error](../cpp/com-raise-error.md)中最多失敗。|  
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|封裝 COM 介面指標，以及自動化所需的呼叫`AddRef`，**發行**，和`QueryInterface`。|  
|[_variant_t](../cpp/variant-t-class.md)|包裝**VARIANT**可提供有用的運算子和方法的型別。|  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器 COM 支援](../cpp/compiler-com-support.md)   
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)   
 [C++ 語言參考](../cpp/cpp-language-reference.md)