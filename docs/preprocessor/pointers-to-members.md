---
title: "pointers_to_members |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
dev_langs: C++
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4e034a268a6ff3c3fc04da4e50a4477324ec1880
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pointerstomembers"></a>pointers_to_members
**C + + 特定的**  
  
 指定類別成員的指標是否可以在其相關類別定義之前宣告，並用來控制解譯指標所需的指標大小和程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## <a name="remarks"></a>備註  
 您可以在放置**pointers_to_members**原始程式檔做為使用替代的 pragma [/vmx](../build/reference/vmb-vmg-representation-method.md)編譯器選項或[繼承關鍵字](../cpp/inheritance-keywords.md)。  
  
 *指標宣告*引數會指定您是指標宣告的成員相關聯函式定義之前或之後。 *指標宣告*引數為下列兩個符號之一：  
  
|引數|註解|  
|--------------|--------------|  
|**full_generality**|產生安全但有時並非是最佳化的程式碼。 您使用**full_generality**如果相關聯的類別定義之前宣告任何成員的指標。 這個引數一律會使用所指定的指標表示*大部分一般表示*引數。 等於 /vmg。|  
|**best_case**|使用所有成員指標的 best-case 表示，產生安全且最佳化的程式碼。 需要在宣告類別成員的指標之前先定義類別。 預設值是**best_case**。|  
  
 *大部分一般表示*引數指定編譯器可以安全地使用任何的轉譯單位中的類別成員指標參考的最小指標表示。 這些引數可以是下列其中一項：  
  
|引數|註解|  
|--------------|--------------|  
|**single_inheritance**|最常見的表示是單一繼承的成員函式指標。 如果宣告其成員指標類別定義的繼承模型為多重或虛擬，則會產生錯誤。|  
|**multiple_inheritance**|最常見的表示是多重繼承的成員函式指標。 如果宣告其成員指標類別定義的繼承模型為虛擬，則會產生錯誤。|  
|**virtual_inheritance**|最常見的表示是虛擬繼承的成員函式指標。 永遠不會產生錯誤。 這是預設引數時**#pragma pointers_to_members**用。|  
  
> [!CAUTION]
>  建議您只將 `pointers_to_members` pragma 放置在您要影響的原始程式碼檔案中，而且只放置在任何 `#include` 指示詞之後。 這種作法可使 pragma 影響到其他檔案的風險降低，否則，您會意外地為相同的變數、函式或類別名稱指定多個定義。  
  
## <a name="example"></a>範例  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## <a name="end-c-specific"></a>END C++ 特定的  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)