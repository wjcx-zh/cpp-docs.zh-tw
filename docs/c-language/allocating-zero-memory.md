---
title: "配置零記憶體 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 010e6b42c2c5ef1cb78fbbf446b77221caf25e14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="allocating-zero-memory"></a>配置零記憶體
**ANSI 4.10.3** `calloc`、`malloc` 或 `realloc` 函式在所要求的大小為零時的行為  
  
 `calloc`、`malloc` 和 `realloc` 函式接受零做為引數。 其中未實際配置記憶體，不過會傳回有效的指標，而且稍後可以藉由 realloc 修改記憶體區塊。  
  
## <a name="see-also"></a>請參閱  
 [程式庫函式](../c-language/library-functions.md)