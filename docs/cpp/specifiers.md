---
title: "規範 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 352ef898c9380c55e90205129ba6fe48bf352856
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="specifiers"></a>規範
本主題描述*decl 規範*（宣告規範） 元件[宣告](declarations-and-definitions-cpp.md)。  
  
 下列預留位置和語言關鍵字為宣告指定名稱：  
  
 *儲存類別規範*  
  
 *類型規範*  
  
 *函式規範*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)  
  
 [__declspec](../cpp/declspec.md) `(` *擴充-decl-修飾詞-seq*`)`  
  
## <a name="remarks"></a>備註  
 *Decl 規範*宣告的一部分是最長串*decl 規範*，就可以採取來表示類型名稱，不包括指標或參考修飾詞。 宣告的其餘部分是*宣告子*，包括導入之名稱。  
  
 下表列出四個宣告，並列出每個宣告*decl 規範*和*宣告子*元件分開。  
  
|宣告|*decl 指定名稱*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|`char`|`*lpszAppName`|  
|`typedef char * LPSTR;`|`char`|`*LPSTR`|  
|`const int func1();`|`const int`|`func1`|  
|`volatile void *pvvObj;`|`volatile void`|`*pvvObj`|  
  
 因為`signed`， `unsigned`， `long`，和`short`全都表示`int`、`typedef`命名為下列其中一個這些關鍵字會被視為屬於*宣告子清單*不屬於*decl 規範*。  
  
> [!NOTE]
>  由於名稱可以重新宣告，因此其解譯會受到目前範圍中最新的宣告所限制。 重新宣告可能會影響編譯器解譯名稱的方式，尤其是 `typedef` 名稱。  
  
## <a name="see-also"></a>請參閱  
 [宣告和定義](declarations-and-definitions-cpp.md)