---
title: 編譯器警告 （層級 1） C4049 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1eea293ff64ed8fe2bf4bf0d38d897eb82223802
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4049"></a>編譯器警告 （層級 1） C4049
編譯器限制： 結束行號發出  
  
 檔案包含多個 16777215 (2<sup>24</sup>-1) 原始程式行。 編譯器會停止在 16777215 編號。  
  
 16777215 行程式碼：  
  
-   映像會包含行號不偵錯資訊。  
  
-   某些診斷可能會報告有不正確的行號。  
  
-   .asm 清單 (/ FAs) 可能不正確的行號。