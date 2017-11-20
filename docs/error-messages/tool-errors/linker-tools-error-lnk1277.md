---
title: "連結器工具錯誤 LNK1277 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1277
dev_langs: C++
helpviewer_keywords: LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 868fb4ef472aaf80242c276a9052562779da745c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1277"></a>連結器工具錯誤 LNK1277
在 pgd （檔名） 中找不到物件記錄  
  
 當使用[/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)，其中一個輸入的.lib、 def、 或.obj 檔案的路徑是在這些期間找到 /ltcg: pginstrument 的路徑不同。 這可能會在 /ltcg: pginstrument 之後說明 LIB 環境變數中的變更。 輸入檔的完整路徑儲存在.pgd 檔案。  
  
 /Ltcg: pgoptimize 會要求輸入在 /ltcg: pginstrument 階段完全相同。  
  
 若要解決這個警告，請執行下列其中一項：  
  
-   執行 /ltcg: pginstrument、 取消復原所有測試回合，並執行 /ltcg: pgoptimize。  
  
-   為您執行 /ltcg: pginstrument 時變更 LIB 環境變數。  
  
 不建議您在使用除了解決 LNK1277。