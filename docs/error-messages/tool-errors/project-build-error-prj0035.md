---
title: 專案建置錯誤 PRJ0035 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0035
dev_langs:
- C++
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd36604763e28fc3f228adec27d0c3775a327d66
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213021"
---
# <a name="project-build-error-prj0035"></a>專案建置錯誤 PRJ0035

> XML 檔案 '*檔案*' 包含無法轉譯為使用者 ANSI 字碼頁的 Unicode 內容。
>
> *檔案的 UNICODE 內容*

*檔案*是為 Web Deployment tool 命令列建立的 XML 檔案。

專案系統無法正確轉譯成 ANSI 的 Web 部署內容頁上某些屬性中找到 Unicode 字元。

此錯誤的解決方法是更新來使用 ANSI，或是在電腦上安裝的字碼頁，並將它設為系統預設值屬性的內容。