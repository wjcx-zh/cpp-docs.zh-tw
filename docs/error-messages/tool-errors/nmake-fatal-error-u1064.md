---
title: "NMAKE 嚴重錯誤 U1064 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20b6c767145176c459d0b70d96842223218cd0b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE 嚴重錯誤 U1064
找不到 MAKEFILE，且沒有指定目標  
  
 NMAKE 命令列中未指定 makefile 或目標，且目前的目錄未包含名為 MAKEFILE 的檔案。  
  
 NMAKE 需要 makefile 框線或命令列的目標 （或兩者都有）。 若要可讓 NMAKE makefile 使用，請指定 /F 選項，或將目前目錄中名為 MAKEFILE 的檔案。 NMAKE 可以使用推斷規則，如果未提供 makefile，來建立命令列的目標。