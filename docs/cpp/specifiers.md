---
title: 指定名稱 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d9898dc6b918643aa8ca4ace34ce2e716344c57
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463485"
---
# <a name="specifiers"></a>規範
本主題描述*decl* （宣告規範） 元件[宣告](declarations-and-definitions-cpp.md)。  
  
 下列預留位置和語言關鍵字為宣告指定名稱：  
  
 *儲存類別規範*  
  
 *類型規範*  
  
 *函式規範*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef]( [typedef](http://msdn.microsod) `(` *擴充-decl-modifier-修飾詞-seq* `)`  
  
## <a name="remarks"></a>備註  
 *Decl*宣告的一部分是最長串*decl* ，可以用來表示類型名稱，不包括指標或參考修飾詞。 宣告的其餘部分*宣告子*，包括引入的名稱。  
  
 下表列出四個宣告，並接著列出每個宣告*decl-modifier 規範*並*宣告子*元件分開。  
  
|宣告|*宣告規範*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|**char**|`*lpszAppName`|  
|`typedef char * LPSTR;`|**char**|`*LPSTR`|  
|`const int func1();`|**const int**|`func1`|  
|`volatile void *pvvObj;`|**volatile void**|`*pvvObj`|  
  
 因為**簽署**，**不帶正負號**，**長**，以及**簡短**全都表示**int**的**typedef**命名為下列其中一個關鍵字會當作成員*declarator-list*不是*decl*。  
  
> [!NOTE]
>  由於名稱可以重新宣告，因此其解譯會受到目前範圍中最新的宣告所限制。 重新宣告可能會影響您如何解譯名稱的編譯器，尤其**typedef**名稱。  
  
## <a name="see-also"></a>另請參閱  
 [宣告和定義](declarations-and-definitions-cpp.md)