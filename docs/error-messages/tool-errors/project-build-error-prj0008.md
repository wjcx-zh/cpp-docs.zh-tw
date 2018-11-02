---
title: 專案建置錯誤 PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 696b77e9906b231a680027a3faaf23e53d8fb6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525897"
---
# <a name="project-build-error-prj0008"></a>專案建置錯誤 PRJ0008

無法刪除檔案 'file'。

**請確定檔案未開啟另一個處理序，並沒有寫入保護。**

Visual c + + 在重建期間，或清除，刪除所有已知中繼和輸出檔案的組建，以及符合萬用字元規格中的任何檔案**要刪除的清除副檔名**屬性中的[一般設定 [設定] 屬性頁](../../ide/general-property-page-project.md)。

如果 Visual c + + 無法刪除檔案，您會看到此錯誤。 若要解決此錯誤，讓檔案和其目錄可寫入執行組建的使用者。