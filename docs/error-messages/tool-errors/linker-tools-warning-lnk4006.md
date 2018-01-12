---
title: "連結器工具警告 LNK4006 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4006
dev_langs: C++
helpviewer_keywords: LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 021961029d274172119ae92aa10cc6a236dd973b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4006"></a>連結器工具警告 LNK4006
符號已定義於物件。忽略第二個定義  
  
 以其裝飾形式顯示的 `symbol` 已定義多次。 這個警告發生時，`symbol`將會加入兩次，但是會使用僅其第一種形式。  
  
 如果您嘗試合併為一個兩個匯入程式庫，您可以取得這項警告。  
  
 如果您要重建 C 執行階段程式庫，您可以忽略此訊息。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  指定`symbol`可能是封裝函式，藉由編譯以建立[/Gy](../../build/reference/gy-enable-function-level-linking.md)。 這個符號已包含在多個檔案，但編譯之間不同。 重新編譯包含的所有檔案`symbol`。  
  
2.  指定`symbol`可能已經定義以不同的方式不同的文件庫中的兩個成員物件中。  
  
3.  絕對可能已經定義了兩次，每個定義在不同的值。  
  
4.  如果合併文件庫時，會收到錯誤訊息`symbol`新增至程式庫中已存在。