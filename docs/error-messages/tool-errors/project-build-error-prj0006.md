---
title: 專案建置錯誤 PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: d62c774411fda80a3e94044b3272567177328ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359653"
---
# <a name="project-build-error-prj0006"></a>專案建置錯誤 PRJ0006

無法開啟暫存檔案 'file'。 請確定檔案存在，而且該目錄沒有寫入保護。

視覺化C++無法在建置流程期間建立暫存檔案。 原因包括：

- 沒有暫存目錄。

- 唯讀的暫存目錄。

- 磁碟空間不足。

- $ （intdir） 資料夾是唯讀，或包含處於唯讀狀態的暫存檔案。

這項錯誤也會發生下列錯誤 PRJ0007:無法建立輸出目錄 'directory'。 錯誤 PRJ0007 表示無法建立 $ （intdir） 目錄，其中隱含建立的暫時檔案也會失敗。

每當您指定時，會建立暫存檔案：

- 回應檔。

- 自訂建置步驟。

- 建置事件。