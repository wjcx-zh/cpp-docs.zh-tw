---
title: "PogoSafeMode | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PogoSafeMode"
ms.assetid: 2daeeff7-44cb-417f-90eb-6b9edf658533
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# PogoSafeMode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定要使用快速模式或安全模式來進行應用程式程式碼剖析。  
  
## 語法  
  
```  
PogoSafeMode  
```  
  
## 備註  
 特性指引最佳化 \(PGO\) 在程式碼剖析階段有兩種可能的模式：快速模式和安全模式。  程式碼剖析處於快速模式時，會使用 **INC** 指令增加資料計數器。  **INC** 指令雖然較快，但不是執行緒安全的。  當程式碼剖析處於安全模式時，會使用 **LOCK INC** 指令增加資料計數器。  **LOCK INC** 指令具有與 **INC** 指令相同的功能，而且是執行緒安全的，但是要比 **INC** 指令緩慢。  
  
 預設情況下，PGO 程式碼剖析會以快速模式操作。  只有在想要使用安全模式時，才會需要 `PogoSafeMode`。  
  
 若要在安全模式中執行 PGO 程式碼剖析，您必須使用環境變數 `PogoSafeMode` 或連結器參數 **\-PogoSafeMode**，視系統而定。  如果您在 x64 電腦上執行程式碼剖析，您就必須使用連結器參數。  如果您在 x86 電腦上執行程式碼剖析，必須在開始最佳化程序之前先定義所有值的環境變數。  
  
## 範例  
  
```  
set PogoSafeMode=1  
```  
  
## 請參閱  
 [特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)   
 [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)