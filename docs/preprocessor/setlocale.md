---
title: "setlocale |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs: C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf0cd4d6d77f4479d5a1cfd56f74f83c3980f38f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setlocale"></a>setlocale
定義轉譯寬字元常數和字串常值時使用的地區設定 (國家/地區和語言)。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma setlocale( "[locale-string]" )  
```  
  
## <a name="remarks"></a>備註  
 由於將多位元組字元轉換為寬字元的演算法因地區設定而異，或者編譯和可執行檔將執行的位置可能使用不同的地區設定，因此這個 pragma 提供在編譯時期指定目標地區設定的方法。 這樣可以確保能夠以正確的格式儲存寬字元字串。  
  
 預設值*地區設定字串*是""。  
  
 「C」地區設定會將字串中的每個字元對應其 `wchar_t` 值 (不帶正負號的短整數)。 適用於其他值`setlocale`中找到這些項目[語言字串](../c-runtime-library/language-strings.md)清單。 例如，您可以發出：  
  
```  
#pragma setlocale("dutch")  
```  
  
 能否發出語言字串取決於電腦的字碼頁和語言 ID 支援。  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)