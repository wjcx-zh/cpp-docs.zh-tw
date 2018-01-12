---
title: "編譯器警告 （層級 1） C4153 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4153
dev_langs: C++
helpviewer_keywords: C4153
ms.assetid: 37a15754-9dba-470b-adda-c4b888064b3e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 73455914be6a49daec3954deb7b5437c4b55305e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4153"></a>編譯器警告 (層級 1) C4153
運算式中函式/資料的指標轉換  
  
 函式指標會轉換成資料指標，反之亦然。 Microsoft 擴充功能 (/Ze) 下允許這項轉換，但 ANSI C 下則不允許。