---
title: "C 執行階段錯誤 R6031 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6031
dev_langs:
- C++
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 260c316ad43ce39a60cb7e54137a363754c1ddf7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6031"></a>C 執行階段錯誤 R6031
嘗試初始化 CRT 一次以上。 這表示您的應用程式中的 bug。  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有發生內部問題。 原因可能是 bug，應用程式中或附加元件或應用程式中使用的擴充功能中的 bug。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**移除，請修復或重新安裝應用程式使用的任何附加元件或延伸程式。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 此診斷指出在載入器鎖定期間執行了 MSIL 指令。 如需詳細資訊，請參閱[初始化的混合的組件](../../dotnet/initialization-of-mixed-assemblies.md)。