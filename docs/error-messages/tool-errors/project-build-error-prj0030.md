---
title: 專案建置錯誤 PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: aa1c8539247287f7644742857c3cb7de321a20a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385390"
---
# <a name="project-build-error-prj0030"></a>專案建置錯誤 PRJ0030

巨集展開發生錯誤。 $（巨集） 的評估遞迴超過 32 個層級。

此錯誤被因為您在巨集中的遞迴。 例如，如果您設定**中繼目錄**屬性 (請參閱[一般屬性頁 （專案）](../../build/reference/general-property-page-project.md)) (IntDir)，您會有遞迴。

若要解決這個錯誤，不會定義巨集或根據它們用來定義的巨集的屬性。