---
title: 推斷規則
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: d3d7ca41d96d3845237b445edefff05044dacdc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170510"
---
# <a name="inference-rules"></a>推斷規則

推斷規則會提供命令來更新目標，以及推斷目標的相依性。 推斷規則中的延伸模組符合具有相同基底名稱的單一目標和相依。 推斷規則是使用者定義或預先定義的;預先定義的規則可以重新定義。

如果過期的相依性沒有任何命令，則為，如果為，則為[。尾碼](dot-directives.md)包含相依的延伸模組，NMAKE 使用的規則，其延伸模組符合目標，以及目前或指定目錄中的現有檔案。 如果有一個以上的規則符合現有的檔案，則為 **。尾碼**清單會決定要使用的值;清單優先順序從左至右遞減。 如果相依檔案不存在，而且未列為另一個描述區塊中的目標，則推斷規則可以從具有相同基底名稱的另一個檔案建立遺漏的相依。 如果描述區塊的目標沒有相依項或命令，則推斷規則可以更新目標。 推斷規則可以建立命令列目標，即使沒有描述區塊存在也一樣。 即使指定明確相依，NMAKE 也可能會叫用推斷相依的規則。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[定義規則](defining-a-rule.md)

[批次模式規則](batch-mode-rules.md)

[預先定義的規則](predefined-rules.md)

[推斷的相依項和規則](inferred-dependents-and-rules.md)

[推斷規則的優先順序](precedence-in-inference-rules.md)

## <a name="see-also"></a>另請參閱

[NMAKE 參考](nmake-reference.md)
