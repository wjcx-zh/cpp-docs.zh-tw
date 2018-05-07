---
title: 專案建置錯誤 PRJ0008 |Microsoft 文件
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
ms.openlocfilehash: 4011a27b7e6707f9c9b4e3ed386306b00f2792cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0008"></a>專案建置錯誤 PRJ0008
無法刪除檔案 'file'。  
  
 **請確定檔案並未開啟另一個處理序，且沒有寫入保護。**  
  
 Visual c + + 期間重建或清除期間，刪除所有已知中繼和輸出檔的組建，以及 符合萬用字元的指定中的任何檔案**要刪除的清除副檔名**屬性[一般組態設定的屬性頁](../../ide/general-property-page-project.md)。  
  
 如果 Visual c + + 無法刪除檔案，您會看到這個錯誤。 若要解決此錯誤，請檔案，其目錄可寫入使用者進行組建。