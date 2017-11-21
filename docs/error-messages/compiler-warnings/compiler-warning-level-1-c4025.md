---
title: "編譯器警告 （層級 1） C4025 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4025
dev_langs: C++
helpviewer_keywords: C4025
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0e9bca6428358d1ce33e8069c7fcdfef19b23c7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4025"></a>編譯器警告 (層級 1) C4025
'number': 基底指標傳遞至擁有變數引數的函式: 參數號碼  
  
 將基底指標傳遞至具有變數引數的函式會導致指標正規化，但結果無法預期。 請不要將基底指標傳遞至具有變數引數的函式。