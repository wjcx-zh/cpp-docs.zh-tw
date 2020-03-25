---
title: 專案建置錯誤 PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 7d1c11ab7539f25d371c0bfbd2853b6155c9661c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192949"
---
# <a name="project-build-error-prj0008"></a>專案建置錯誤 PRJ0008

無法刪除檔案 ' file '。

**請確認檔案未被其他進程開啟，而且不受寫入保護。**

在重建或清除期間，視覺C++效果會刪除組建的所有已知中繼和輸出檔案，以及符合 [[一般設定] 屬性頁](../../build/reference/general-property-page-project.md)中 [**清除時要刪除的副檔名**] 內容中萬用字元規格的任何檔案。

如果 Visual C++無法刪除檔案，您將會看到此錯誤。 若要解決此錯誤，請讓檔案及其目錄可供執行組建的使用者寫入。
