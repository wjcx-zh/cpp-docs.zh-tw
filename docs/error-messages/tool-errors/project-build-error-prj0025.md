---
title: 專案建置錯誤 PRJ0025 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0025
dev_langs:
- C++
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 949e36424fc213459e56332c0802d2719581bac1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209808"
---
# <a name="project-build-error-prj0025"></a>專案建置錯誤 PRJ0025

> 批次檔 '*檔案*' 包含無法轉譯為使用者 ANSI 字碼頁的 Unicode 內容。
>
> *檔案的 UNICODE 內容*

專案系統找到 Unicode 內容中自訂建置規則，或建置無法正確轉譯成使用者的目前的 ANSI 字碼頁的事件。

此錯誤的解決方法是更新的建置規則的內容，或建置事件，來使用 ANSI，或是在電腦上安裝的字碼頁，並將它設為系統預設值。

如需有關自訂建置步驟和建置事件，請參閱[了解自訂建置步驟和建置事件](../../ide/understanding-custom-build-steps-and-build-events.md)。