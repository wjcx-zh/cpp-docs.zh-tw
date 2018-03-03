---
title: "嚴重錯誤 C1061 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1061
dev_langs:
- C++
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81963b0fffdf1b86b56b10c0776874b37ae9daa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1061"></a>嚴重錯誤 C1061
編譯器限制：區塊巢狀結構太深  
  
 程式碼區塊的巢狀結構超過 128 層的限制。 這是在 32 位元和 64 位元工具集中，C 和 C++ 編譯器的一種硬性限制。 任何建立範圍或區塊的項目皆會增加巢狀層次的計數。 例如，命名空間、using 指示詞、前置處理器展開、範本展開、例外狀況處理、迴圈建構及 else-if 子句，皆可能呼叫增加編譯器所看到的巢狀層次。  
  
 若要更正這個錯誤，您必須重構程式碼。 在任何情況下，深度巢狀程式碼都不容易了解及說明。 重構程式碼以減少巢狀層次，如可改善程式碼品質，並簡化維護工作。 將深度巢狀程式碼分為從原始內容呼叫的函式。 限制區塊中迴圈數目或鏈結的 else-if 子句。