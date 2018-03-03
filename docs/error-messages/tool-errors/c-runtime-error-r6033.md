---
title: "C 執行階段錯誤 R6033 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6033
dev_langs:
- C++
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f2ef73d3cb82a65c8114d2e7f921b47ffd45d65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6033"></a>C 執行階段錯誤 R6033
嘗試使用從原生程式碼初始化期間這個組件的 MSIL 程式碼。 這表示您的應用程式中的 bug。 最有可能是呼叫 MSIL 編譯的結果 (/ clr) 函式從原生的建構函式，或從 DllMain。  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有發生內部問題。 應用程式中的 bug 或增益集或擴充功能，它會使用中的錯誤，可能造成這個錯誤。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**移除，請修復或重新安裝任何擴充功能或增益集。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 此診斷指出在載入器鎖定期間執行了 MSIL 指令。 如果您要使用 /clr 旗標編譯原生 c + +，也可能會發生。 只能在包含 managed 程式碼的模組上使用 /clr 旗標。 如需詳細資訊，請參閱[初始化的混合的組件](../../dotnet/initialization-of-mixed-assemblies.md)。