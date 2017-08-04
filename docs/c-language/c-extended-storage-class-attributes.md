---
title: "C 擴充的儲存類別屬性 | Microsoft Docs"
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
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
caps.latest.revision: 9
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
ms.openlocfilehash: e79b08ebba48221e8666ced75875a68f06bf2df3
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="c-extended-storage-class-attributes"></a>C 擴充的儲存類別屬性
**Microsoft 特定的**  
  
 有關本主題的最新資訊可以在 [__declspec (C++ 參考)](../cpp/declspec.md) 中找到。  
  
 擴充屬性語法可簡化並標準化 Microsoft 專有的 C 語言擴充功能。 使用擴充屬性語法的儲存類別屬性包括 thread、naked、dllimport 及 dllexport。  
  
 用於指定儲存類別資訊的擴充屬性語法會使用 __declspec 關鍵字，這個關鍵字會指定特定類型的執行個體要以 Microsoft 專有儲存類別屬性儲存 (thread、naked、dllimport 或 dllexport)。 其他儲存類別修飾詞的範例包括 static 和 extern 關鍵字。 不過，這些關鍵字是 ANSI C 標準的一部分，因此未涵蓋在擴充屬性語法內。  
  
## <a name="syntax"></a>語法  
 *storage-class-specifier*：  
 `__declspec` ( *extended-decl-modifier-seq* ) /* Microsoft 特定的 \*/  
  
 *extended-decl-modifier-seq*:  
 *extended-decl-modifier* opt  
  
 *extended-decl-modifier-seq extended-decl-modifier*  
  
 *extended-decl-modifier*:  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
 空白字元用於分隔宣告修飾詞。 請注意，*extended-decl-modifier-seq* 可以是空的，在這種情況下，__declspec 沒有作用。  
  
 thread、naked、dllimport 和 dllexport 儲存類別屬性 (Attribute) 是只屬於其套用所在資料或函式宣告的屬性 (Property)，這些屬性 (Attribute) 並不會重新定義函式本身的類別屬性 (Attribute)。 thread 屬性只會影響資料。 naked 屬性只會影響函式。 dllimport 和 dllexport 屬性會同時影響函式和資料。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [宣告和類型](../c-language/declarations-and-types.md)
