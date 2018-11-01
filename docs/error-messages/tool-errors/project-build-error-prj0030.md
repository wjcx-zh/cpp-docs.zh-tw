---
title: 專案建置錯誤 PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 2a6cde4ca48acb9aadfe3109084483dbb554e1e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488071"
---
# <a name="project-build-error-prj0030"></a>專案建置錯誤 PRJ0030

巨集展開發生錯誤。 $（巨集） 的評估遞迴超過 32 個層級。

此錯誤被因為您在巨集中的遞迴。 例如，如果您設定**中繼目錄**屬性 (請參閱[一般屬性頁 （專案）](../../ide/general-property-page-project.md)) (IntDir)，您會有遞迴。

若要解決這個錯誤，不會定義巨集或根據它們用來定義的巨集的屬性。