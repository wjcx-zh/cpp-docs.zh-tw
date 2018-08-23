---
title: 內建函式和內嵌組譯 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff2b99eedcdd81a96dc3091046a4f62ffe002509
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572813"
---
# <a name="intrinsics-and-inline-assembly"></a>內建和內嵌組譯
其中一個條件約束，適用於 x64 編譯器會為沒有內嵌組譯工具支援。 函式，這表示無法寫入 C 或 c + + 中是必須可寫入為副程式或編譯器所支援的內建函式。 某些函式是效能敏感，而有些則不。 重視效能的函式應該實作為內建函式。  
  
 編譯器所支援的內建函式中所述[編譯器內建](../intrinsics/compiler-intrinsics.md)。  
  
## <a name="see-also"></a>另請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)