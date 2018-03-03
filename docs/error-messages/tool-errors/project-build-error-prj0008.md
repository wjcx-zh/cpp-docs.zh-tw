---
title: "專案建置錯誤 PRJ0008 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1740b0cf1edfc90258de4fe26478298ddf2875c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0008"></a>專案建置錯誤 PRJ0008
無法刪除檔案 'file'。  
  
 **請確定檔案並未開啟另一個處理序，且沒有寫入保護。**  
  
 Visual c + + 期間重建或清除期間，刪除所有已知中繼和輸出檔的組建，以及 符合萬用字元的指定中的任何檔案**要刪除的清除副檔名**屬性[一般組態設定的屬性頁](../../ide/general-property-page-project.md)。  
  
 如果 Visual c + + 無法刪除檔案，您會看到這個錯誤。 若要解決此錯誤，請檔案，其目錄可寫入使用者進行組建。