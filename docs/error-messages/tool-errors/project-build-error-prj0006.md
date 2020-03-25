---
title: 專案建置錯誤 PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: 816355276a203adba1401841ce02eb94a18085b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192779"
---
# <a name="project-build-error-prj0006"></a>專案建置錯誤 PRJ0006

無法開啟暫存檔案 ' file '。 請確定檔案存在，而且目錄不受寫入保護。

視覺C++效果無法在建立程式期間建立暫存檔案。 原因包括：

- 沒有臨時目錄。

- 唯讀臨時目錄。

- 磁碟空間不足。

- $ （IntDir）資料夾可能是唯讀的，或是包含唯讀的暫存檔案。

此錯誤也會發生在錯誤 PRJ0007：無法建立輸出目錄 ' directory '。 錯誤 PRJ0007 表示無法建立 $ （IntDir）目錄，也就是說，暫時檔案的建立也會失敗。

每當您指定時，就會建立暫存檔案：

- 回應檔。

- 自訂的組建步驟。

- 組建事件。
