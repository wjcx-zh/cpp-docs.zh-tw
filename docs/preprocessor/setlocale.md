---
title: setlocale |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs:
- C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cfabfa3c83fe2ff90a6f7dbe07d5205f7a6f9a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847412"
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
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)