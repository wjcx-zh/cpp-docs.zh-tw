---
title: 專案建置錯誤 PRJ0035
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: 8486c4f62f637f6f7e9826a289c21f8f194eb9f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192168"
---
# <a name="project-build-error-prj0035"></a>專案建置錯誤 PRJ0035

> XML 檔案 '*file*' 包含無法轉譯為使用者 ANSI 字碼頁的 Unicode 內容。
>
> *檔案的 UNICODE 內容*

檔案*是以*命令列形式建立給 Web 部署工具的 XML 檔案。

專案系統在 Web 部署屬性頁的某個屬性中找到 Unicode 字元，但無法正確轉譯為 ANSI。

此錯誤的解決方法是將屬性的內容更新為使用 ANSI，或將字碼頁安裝在您的電腦上，並將它設定為系統預設值。
