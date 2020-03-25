---
title: 專案建置錯誤 PRJ0025
ms.date: 08/27/2018
f1_keywords:
- PRJ0025
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
ms.openlocfilehash: 30445a3abc2a6ad05c983448f57ed5b93df6e61f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192350"
---
# <a name="project-build-error-prj0025"></a>專案建置錯誤 PRJ0025

> 批次檔 '*file*' 包含無法轉譯為使用者 ANSI 字碼頁的 Unicode 內容。
>
> *檔案的 UNICODE 內容*

專案系統在自訂群組建規則或組建事件中發現 Unicode 內容，無法正確轉譯成使用者目前的 ANSI 字碼頁。

此錯誤的解決方法是將組建規則或組建事件的內容更新為使用 ANSI，或將字碼頁安裝在您的電腦上，並將它設定為系統預設值。

如需自訂群組建步驟和組建事件的詳細資訊，請參閱[瞭解自訂群組建步驟和組建事件](../../build/understanding-custom-build-steps-and-build-events.md)。
