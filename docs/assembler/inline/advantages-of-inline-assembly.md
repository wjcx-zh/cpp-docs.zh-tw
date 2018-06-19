---
title: 內嵌組譯碼的優點 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 998ec5ff04911d3e476f0864f81f82b804969a82
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051703"
---
# <a name="advantages-of-inline-assembly"></a>內嵌組譯碼的優點
## <a name="microsoft-specific"></a>Microsoft 特定的  
 因為內嵌組合不需要個別的組譯及連結步驟，所以比個別進行組譯方便。 內嵌組合語言程式碼可以使用範圍內的任何 C 變數或函式名稱，因此很容易就能與您程式的 C 程式碼整合。 因為組譯程式碼可以透過內嵌方式與 C 或 C++ 陳述式混用，因此可以執行在 C 或 C++ 中相當麻煩或無法執行的工作。  
  
 內嵌組譯碼的用法包括：  
  
-   以組合語言撰寫函式。  
  
-   對程式碼的速度關鍵區段進行位置最佳化。  
  
-   讓裝置驅動程式直接存取硬體。  
  
-   撰寫 "naked" 呼叫的初構和終解程式碼。  
  
 內嵌組譯碼是具有特殊用途的工具。 如果您打算將應用程式移植到不同的電腦上，可能會想要將電腦專屬的程式碼放在不同的模組中。 由於內嵌組譯碼並未支援全部的 Microsoft Macro Assembler (MASM) 巨集和資料指示詞，因此針對這類模組使用 MASM 可能會更方便。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [內嵌組合語言](../../assembler/inline/inline-assembler.md)