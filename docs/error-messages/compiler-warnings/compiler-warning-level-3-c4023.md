---
title: "編譯器警告 （層級 3） C4023 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4023
dev_langs: C++
helpviewer_keywords: C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e22ba0ed3d91f75ba73e68817611302d15fa2039
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4023"></a>編譯器警告 (層級 3) C4023
'symbol' : 基底指標傳送至沒有原型的函式 : 參數號碼  
  
 將基底指標傳送至沒有原型的函式會導致指標正規化，但結果無法預期。  
  
 如果您針對要傳送的基底指標使用原型函式，則可以修正這個警告。