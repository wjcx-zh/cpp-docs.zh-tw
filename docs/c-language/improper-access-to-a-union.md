---
title: 不適當的等位存取 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c322ff9e411cc6c9ef845fdd9a289a9ed5c49d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="improper-access-to-a-union"></a>不適當的等位存取
**ANSI 3.3.2.3**：使用不同類型的成員存取等位物件的成員  
  
 如果宣告了兩種類型的等位並且儲存一個值，但等位是以另一種類型存取，則結果不可靠。  
  
 例如，宣告了 **float** 與 `int` 的等位。 儲存了 **float** 值，但是程式之後將值當作 `int` 來存取。 在這種情況下，值會取決於 **float** 值的內部儲存區。 整數值會變得不可靠。  
  
## <a name="see-also"></a>請參閱  
 [結構、等位、列舉和位元欄位](../c-language/structures-unions-enumerations-and-bit-fields.md)