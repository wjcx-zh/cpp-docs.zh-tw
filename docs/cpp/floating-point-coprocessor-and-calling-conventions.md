---
title: 浮點常數副處理器和呼叫慣例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66ccd54c4abb1d8d9761d5ded88beba76bfae043
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401350"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮點常數副處理器和呼叫慣例
如果您要為浮點常式點副處理器撰寫組件，您必須保留浮點控制字詞並清除副處理器堆疊，除非您要傳回**浮點數**或是**double**值 （也就您的函式應在 ST(0 中傳回。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)