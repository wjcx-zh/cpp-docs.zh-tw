---
title: 專案建置錯誤 PRJ0030 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964fedd40f577a8b337c4ad0c20ba80d33ed2a23
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099896"
---
# <a name="project-build-error-prj0030"></a>專案建置錯誤 PRJ0030

巨集展開發生錯誤。 $（巨集） 的評估遞迴超過 32 個層級。

此錯誤被因為您在巨集中的遞迴。 例如，如果您設定**中繼目錄**屬性 (請參閱[一般屬性頁 （專案）](../../ide/general-property-page-project.md)) (IntDir)，您會有遞迴。

若要解決這個錯誤，不會定義巨集或根據它們用來定義的巨集的屬性。