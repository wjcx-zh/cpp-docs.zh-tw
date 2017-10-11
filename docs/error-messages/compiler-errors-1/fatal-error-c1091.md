---
title: "嚴重錯誤 C1091 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 6c3fd2dae1f3258ce90d30c78792c498be75615a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1091"></a>嚴重錯誤 C1091
編譯器限制：字串長度超過 'length' 個位元組的上限  
  
 字串常數超過目前的字串長度限制。  
  
 您可能想要將靜態字串分割成兩個 (含) 以上的變數，並使用 [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 將結果聯結作為宣告的一部分或在執行階段時聯結。
