---
title: "執行 NMAKE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a6c39612cf4df47665f7ea3d529b77ee4e70ce8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="running-nmake"></a>執行 NMAKE
## <a name="syntax"></a>語法  
  
```  
NMAKE [option...] [macros...] [targets...] [@commandfile...]  
```  
  
## <a name="remarks"></a>備註  
 只有指定 NMAKE 組建*目標*或未指定，如果第一個目標 makefile 中的。 第一個 makefile 目標可以是[虛擬目標](../build/pseudotargets.md)來建置其他目標。 NMAKE 使用 /F; 使用指定的 makefile如果未指定 /F，它會使用 Makefile 中的檔案目前的目錄。 如果未不指定任何 makefile，建置命令列使用推斷規則*目標*。  
  
 `commandfile`文字檔案 （或回應檔） 包含命令列輸入。 其他輸入可以前面或後面的`commandfile`。 允許的路徑。 在`commandfile`，分行符號會被視為空格。 如果包含空格，請將巨集括在引號中。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
 [NMAKE 選項](../build/nmake-options.md)  
  
 [Tools.ini 和 NMAKE](../build/tools-ini-and-nmake.md)  
  
 [NMAKE 的結束代碼](../build/exit-codes-from-nmake.md)  
  
## <a name="see-also"></a>請參閱  
 [NMAKE 參考](../build/nmake-reference.md)