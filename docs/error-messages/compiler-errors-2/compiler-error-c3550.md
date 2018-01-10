---
title: "編譯器錯誤 C3550 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3550
dev_langs: C++
helpviewer_keywords: C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a05f0fc0b16cd7e3da851cb696f0ff60b8498319
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3550"></a>編譯器錯誤 C3550
此內容中不得有純 'decltype(auto)'  
  
 如果 `decltype(auto)` 做為函式傳回類型的預留位置，則必須由本身使用。 它不能在指標宣告 (`decltype(auto*)`)、參考宣告 (`decltype(auto&)`) 或任何其他這類限定性條件中使用。  
  
## <a name="see-also"></a>請參閱  
 [auto](../../cpp/auto-cpp.md)