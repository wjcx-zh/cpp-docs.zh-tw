---
title: "編譯器警告 （層級 1） C4182 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4182
dev_langs: C++
helpviewer_keywords: C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ef78cebafcb07977611f92ad9f49a3d5b2c3dde
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4182"></a>編譯器警告 (層級 1) C4182
\#包含巢狀層級深度; 具有 'number'可能有無限遞迴  
  
 編譯器已用完堆積上的空間，因為巢狀 Include 檔數目太多。 當從另一個 Include 檔包含 Include 檔時即為巢狀 Include 檔。  
  
 這個訊息僅供參考，而且前面出現錯誤 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)。