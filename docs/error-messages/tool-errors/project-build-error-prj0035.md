---
title: 專案建置錯誤 PRJ0035
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: e221fd85f1260ed04d49b43dea3d13407f504847
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345301"
---
# <a name="project-build-error-prj0035"></a>專案建置錯誤 PRJ0035

> XML 檔案 '*檔案*' 包含無法轉譯為使用者 ANSI 字碼頁的 Unicode 內容。
>
> *檔案的 UNICODE 內容*

*檔案*是為 Web Deployment tool 命令列建立的 XML 檔案。

專案系統無法正確轉譯成 ANSI 的 Web 部署內容頁上某些屬性中找到 Unicode 字元。

此錯誤的解決方法是更新來使用 ANSI，或是在電腦上安裝的字碼頁，並將它設為系統預設值屬性的內容。