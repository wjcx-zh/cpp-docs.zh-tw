---
title: "Visual C++ 64 位元移轉時常見的問題 | Microsoft Docs"
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
  - "32 位元程式碼移植 [C++]"
  - "64 位元應用程式 [C++]"
  - "64 位元編譯器 [C++], 移轉"
  - "64 位元編譯器 [C++], 移轉 32 位元程式碼"
  - "64 位元程式設計 [C++], 移轉"
  - "移轉 [C++], 64 位元的程式碼問題"
  - "移植 32 位元程式碼至 64 位元程式碼"
  - "升級 Visual C++ 應用程式, 32 位元的程式碼"
  - "Win64 [C++]"
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 64 位元移轉時常見的問題
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用 Visual c\+\+ 建立在 64 位元 Windows 作業系統上執行的應用程式時，您應注意下列問題：  
  
-   `int` 和 `long` 是 64 位元 Windows 作業系統上的 32 位元值。  對於您要為 64 位元平台進行編譯的程式，您應小心不要將指標指派給 32 位元變數。  指標在 64 位元平台上是 64 位元的，如果您將指標指派給 32 位元變數，將會截斷指標值。  
  
-   `size_t`、`time_t` 和  `ptrdiff_t` 在 64 位元 Windows 作業系統上是 64 位元值。  
  
-   在 32 位元 Windows 作業系統上，`time_t` 在 Visual C\+\+ 2005 之前的 Visual C\+\+ 版本中是 32 位元值。  `time_t` 現在預設為 64 位元整數。  如需詳細資訊，請參閱[時間管理](../c-runtime-library/time-management.md)。  
  
     您應注意程式碼在何處取用 `int` 值，並將其視為 `size_t` 或 `time_t` 值來處理。  此數值可能會成長而大於 32 位元數值，且資料在傳回至 `int` 儲存體時將會截斷。  
  
 %x \(十六進位 `int` 格式\) `printf` 修飾詞在 64 位元 Windows 作業系統上將無法如預期運作。  它只會處理傳遞給它之值的前 32 個位元。  
  
-   使用 %I32x 可顯示十六進位格式的 32 位元整數類型。  
  
-   使用 %I64x 顯示十六進位格式的 64 位元整數類型。  
  
-   %p \(指標的十六進位格式\) 在 64 位元 Windows 作業系統上將如預期運作。  
  
 如需詳細資訊，請參閱:  
  
-   [編譯器選項](../build/reference/compiler-options.md)  
  
-   [\<caps:sentence id\="tgt18" sentenceid\="8228b16e9fef41dbba1af1d78bf0cc87" class\="tgtSentence"\>移轉提示\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/aa384214)  
  
## 請參閱  
 [為 64 位元設定程式](../build/configuring-programs-for-64-bit-visual-cpp.md)   
 [移植您的程式](http://msdn.microsoft.com/zh-tw/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)