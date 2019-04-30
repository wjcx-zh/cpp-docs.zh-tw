---
title: 專案建置錯誤 PRJ0025
ms.date: 08/27/2018
f1_keywords:
- PRJ0025
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
ms.openlocfilehash: 5f3699dce75a20b9cc6e1d712bc5702543ab7b6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383942"
---
# <a name="project-build-error-prj0025"></a>專案建置錯誤 PRJ0025

> 批次檔 '*檔案*' 包含無法轉譯為使用者 ANSI 字碼頁的 Unicode 內容。
>
> *檔案的 UNICODE 內容*

專案系統找到 Unicode 內容中自訂建置規則，或建置無法正確轉譯成使用者的目前的 ANSI 字碼頁的事件。

此錯誤的解決方法是更新的建置規則的內容，或建置事件，來使用 ANSI，或是在電腦上安裝的字碼頁，並將它設為系統預設值。

如需有關自訂建置步驟和建置事件，請參閱[了解自訂建置步驟和建置事件](../../build/understanding-custom-build-steps-and-build-events.md)。