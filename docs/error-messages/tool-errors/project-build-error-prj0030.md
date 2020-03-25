---
title: 專案建置錯誤 PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 3675c3796ae37df848e458aa2db665d8c4aa7766
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192506"
---
# <a name="project-build-error-prj0030"></a>專案建置錯誤 PRJ0030

宏展開錯誤。 評估 $ （宏）的遞迴超過32層級。

這個錯誤是由宏中的遞迴所造成。 例如，如果您將 [**中繼目錄**] 屬性（請參閱[一般屬性頁（專案）](../../build/reference/general-property-page-project.md)）設定為 $ （IntDir），則會有遞迴。

若要解決這個錯誤，請不要以它們用來定義的宏來定義宏或屬性。
