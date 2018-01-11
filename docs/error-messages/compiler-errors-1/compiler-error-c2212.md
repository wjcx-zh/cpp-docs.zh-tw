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
ms.workload: cplusplus
ms.openlocfilehash: 0c49161940c1f382a8bf9d82a648cc4396a11e86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2212"></a>編譯器錯誤 C2212
'identifier': __based 不提供函式指標  
  
 函式的指標不可以宣告為`__based`。 如果您需要的程式碼為基礎的資料，請使用`__declspec`關鍵字或`data_seg`pragma。