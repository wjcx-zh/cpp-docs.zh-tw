---
title: 專案建置錯誤 PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 5741b7ef8cb9a7ae53d64874d3531e9271c09e0f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815992"
---
# <a name="project-build-error-prj0008"></a>專案建置錯誤 PRJ0008

無法刪除檔案 'file'。

**請確定檔案未開啟另一個處理序，並沒有寫入保護。**

Visual c + + 在重建期間，或清除，刪除所有已知中繼和輸出檔案的組建，以及符合萬用字元規格中的任何檔案**要刪除的清除副檔名**屬性中的[一般設定 [設定] 屬性頁](../../build/reference/general-property-page-project.md)。

如果 Visual c + + 無法刪除檔案，您會看到此錯誤。 若要解決此錯誤，讓檔案和其目錄可寫入執行組建的使用者。