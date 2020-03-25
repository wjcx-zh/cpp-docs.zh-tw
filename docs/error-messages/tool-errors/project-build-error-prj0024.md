---
title: 專案建置錯誤 PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: bcfdcce54618acca0e22daa54e95083cf3ee9d50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192610"
---
# <a name="project-build-error-prj0024"></a>專案建置錯誤 PRJ0024

> Unicode 路徑 '*path*' 無法轉譯成使用者的 ANSI 字碼頁。

*path*是路徑字串的原始 Unicode 版本。 如果有 Unicode 路徑無法直接轉譯為目前系統字碼頁的 ANSI，就會發生這個錯誤。

如果您使用的專案是使用不在電腦上的字碼頁所開發的，則可能會發生這個錯誤。

此錯誤的解決方式是更新路徑以使用 ANSI 文字，或在您的電腦上安裝字碼頁，並將其設定為系統預設值。
