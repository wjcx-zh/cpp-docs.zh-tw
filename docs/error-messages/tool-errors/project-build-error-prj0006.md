---
title: 專案建置錯誤 PRJ0006 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 264b2f90a2d778b1545117ce5c3b1272626ebad6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073248"
---
# <a name="project-build-error-prj0006"></a>專案建置錯誤 PRJ0006

無法開啟暫存檔案 'file'。 請確定檔案存在，而且該目錄沒有寫入保護。

Visual c + + 無法在建置流程期間建立暫存檔案。 原因包括：

- 沒有暫存目錄。

- 唯讀的暫存目錄。

- 磁碟空間不足。

- $ （intdir） 資料夾是唯讀，或包含處於唯讀狀態的暫存檔案。

這項錯誤也會發生下列錯誤 PRJ0007： 無法建立輸出目錄 'directory'。 錯誤 PRJ0007 表示無法建立 $ （intdir） 目錄，其中隱含建立的暫時檔案也會失敗。

每當您指定時，會建立暫存檔案：

- 回應檔。

- 自訂建置步驟。

- 建置事件。