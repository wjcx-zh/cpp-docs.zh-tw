---
title: "編譯器警告 （層級 4） C4960 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4960
dev_langs: C++
helpviewer_keywords: C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 160ae5a50d55ab0ebc89335aa3951aa781175feb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4960"></a>編譯器警告 (層級 4) C4960
'function' 太大而無法分析  
  
 使用 [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)時，編譯器偵測到函式大於 65,535 個指令的輸入模組。 這類大型函式不適用於特性指引最佳化。  
  
 若要解決這個警告，請減少函式的大小。