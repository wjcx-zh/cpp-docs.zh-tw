---
title: "資源編譯器警告 RW4004 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0249f7d01ee344f0fa17bdc39e58e9fce26c9b25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rw4004"></a>資源編譯器警告 RW4004
ASCII 字元不等同虛擬按鍵碼  
  
 針對 VIRTKEY 類型快速鍵中的虛擬按鍵碼使用了字串常值。  
  
 這則警告允許您繼續進行；但請注意，所產生的快速鍵可能不符合您指定的字串 (VIRTKEY 使用不同於 ASCII 快速鍵的按鍵碼)。  
  
 雖然字串常值的語法有效，才能確保您能取得您想要使用的快速鍵**VK_\* #define**在 WINDOWS.h 中的值。