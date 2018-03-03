---
title: "編譯器警告 (層級 1) C4729 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57d6d5dc95ce3ef9cf4890b93ef1ab3abe2d6601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4729"></a>編譯器警告 (層級 1) C4729
依據 flow graph 產生的警告，發現函式太大  
  
 如果要編譯的函式太大，無法可靠地檢查將產生警告的情況，則會產生這個警告。 使用 [/Od](../../build/reference/od-disable-debug.md) 編譯器選項時，才會產生這個警告。  
  
 若要解決這個警告，請將函式分為較小的函式。