---
title: 專案建置錯誤 PRJ0026
ms.date: 08/27/2018
f1_keywords:
- PRJ0026
helpviewer_keywords:
- PRJ0026
ms.assetid: c52bc9b5-8b22-4015-b477-8645ae56c489
ms.openlocfilehash: 9193d91d6abd3b1c9a4fbac1e3c50c045658ddff
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192272"
---
# <a name="project-build-error-prj0026"></a>專案建置錯誤 PRJ0026

> 回應檔 '*file*' 包含無法轉譯為使用者 ANSI 字碼頁的 Unicode 內容。
>
> *檔案的 UNICODE 內容*

專案系統在回應檔中找到 Unicode 內容，但該檔案無法正確轉譯成使用者的目前 ANSI 字碼頁。

此錯誤的解決方法是將回應檔的內容更新為使用 ANSI，或將字碼頁安裝在您的電腦上，並將它設定為系統預設值。
