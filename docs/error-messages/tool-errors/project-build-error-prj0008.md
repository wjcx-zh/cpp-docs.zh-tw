---
title: 專案建置錯誤 PRJ0008 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7c24634a845423de590228af01cb9f4779e37ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062783"
---
# <a name="project-build-error-prj0008"></a>專案建置錯誤 PRJ0008

無法刪除檔案 'file'。

**請確定檔案未開啟另一個處理序，並沒有寫入保護。**

Visual c + + 在重建期間，或清除，刪除所有已知中繼和輸出檔案的組建，以及符合萬用字元規格中的任何檔案**要刪除的清除副檔名**屬性中的[一般設定 [設定] 屬性頁](../../ide/general-property-page-project.md)。

如果 Visual c + + 無法刪除檔案，您會看到此錯誤。 若要解決此錯誤，讓檔案和其目錄可寫入執行組建的使用者。