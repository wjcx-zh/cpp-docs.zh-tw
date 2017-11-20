---
title: "編譯器錯誤 C2212 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2212
dev_langs: C++
helpviewer_keywords: C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8515302c7b794a92fe16f3c0baf9c82665aa4d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2212"></a>編譯器錯誤 C2212
'identifier': __based 不提供函式指標  
  
 函式的指標不可以宣告為`__based`。 如果您需要的程式碼為基礎的資料，請使用`__declspec`關鍵字或`data_seg`pragma。