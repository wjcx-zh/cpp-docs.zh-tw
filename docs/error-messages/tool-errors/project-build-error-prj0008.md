---
title: 專案建置錯誤 PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 5741b7ef8cb9a7ae53d64874d3531e9271c09e0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359484"
---
# <a name="project-build-error-prj0008"></a>專案建置錯誤 PRJ0008

無法刪除檔案 'file'。

**請確定檔案未開啟另一個處理序，並沒有寫入保護。**

在重建期間或乾淨、 VisualC++會刪除所有已知中繼和輸出檔案的組建，以及符合萬用字元規格中的任何檔案**延伸模組時要刪除的清除**中的屬性[一般組態設定 屬性頁](../../build/reference/general-property-page-project.md)。

您會看到這個錯誤，如果 VisualC++無法刪除檔案。 若要解決此錯誤，讓檔案和其目錄可寫入執行組建的使用者。