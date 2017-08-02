---
title: "不適當的等位存取 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 9e3bd236cfc6675f9476a0127977e329af3698af
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="improper-access-to-a-union"></a>不適當的等位存取
**ANSI 3.3.2.3**：使用不同類型的成員存取等位物件的成員  
  
 如果宣告了兩種類型的等位並且儲存一個值，但等位是以另一種類型存取，則結果不可靠。  
  
 例如，宣告了 **float** 與 `int` 的等位。 儲存了 **float** 值，但是程式之後將值當作 `int` 來存取。 在這種情況下，值會取決於 **float** 值的內部儲存區。 整數值會變得不可靠。  
  
## <a name="see-also"></a>另請參閱  
 [結構、等位、列舉和位元欄位](../c-language/structures-unions-enumerations-and-bit-fields.md)
