---
title: 屬性內容 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e3935b168220b528afaecd2e1438cfe49496b1b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313659"
---
# <a name="attribute-contexts"></a>屬性內容
C + + 屬性可以使用四個基本的欄位描述： 它們可以套用到目標 (**適用於**)，如果它們是可重複，或是不 (**Repeatable**)、 所需的其他屬性 (存在**所需的屬性**)，和不相容性與其他屬性 (**無效的屬性**)。 隨附的資料表中每個屬性的參考主題會列出這些欄位。 以下說明每個欄位。
  
## <a name="applies-to"></a>適用於
 此欄位會描述所指定之屬性的合法目標的不同 c + + 語言項目。 比方說，如果屬性會指定 「 類別 」 中**套用至** 欄位中，這會指出屬性只能套用至合法的 c + + 類別。 如果屬性套用至類別的成員函式，會產生語法錯誤。
  
 如需詳細資訊，請參閱 <<c0> [ 屬性的用法](../windows/attributes-by-usage.md)。
  
## <a name="repeatable"></a>可重複
 此欄位會指出是否將屬性可以重複套用至相同的目標。 大部分的屬性不是可重複的。
  
## <a name="required-attributes"></a>必要屬性
 此欄位會列出其他要使用的屬性才能正確執行指定之屬性的存在 （亦即，套用至相同的目標）。 是常見的此欄位的任何項目屬性。
  
## <a name="invalid-attributes"></a>無效的屬性
 此欄位會列出與指定的屬性不相容的其他屬性。 是常見的此欄位的任何項目屬性。
  
## <a name="see-also"></a>另請參閱
 [C++ 屬性參考](../windows/cpp-attributes-reference.md)