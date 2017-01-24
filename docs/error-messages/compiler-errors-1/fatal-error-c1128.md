---
title: "嚴重錯誤 C1128 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1128"
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1128
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

區段數目超過目的檔格式的限制 : 請以 \/bigobj 編譯  
  
 .obj 檔超過可容許的區段數，即超過 COFF 目的檔格式限制。  
  
 可能是因為使用 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 和偵錯組建，才導致超過此區段限制；**\/Gy** 會使函式進入其本身的 COMDAT 區段中。  在偵錯組建中，每個 COMDAT 函式都有一個偵錯資訊區段。  
  
 若有過多的內嵌 \(Inline\) 函式時，也會發生 C1128。  
  
 若要更正此錯誤，請將原始程式檔分成多個原始程式碼檔，編譯時不使用 **\/Gy**，或是使用 [\/bigobj \(增加 .Obj 檔中的區段數目\)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md) 編譯。如果不使用 **\/Gy** 編譯，就必須各個檔分別指定最佳化，因為 **\/O2** 和 **\/O1** 都隱含 **\/Gy**。  
  
 請盡可能在沒有偵錯資訊下進行編譯。  
  
 您也可能必須有各個不同原始程式檔中的特定樣板資訊，而不要讓編譯器各個發出。  
  
 當移植程式碼時，使用 x64 編譯器， C1128 有可能先出現，而使用 x86 編譯器的會比較慢出現。x64 至少 4 個區段會與每個用 **\/Gy** 編譯的函式相關連或範本內嵌或類別內嵌: 程式碼，pdata 和偵錯資訊，也可能和 xdata。X86 則不會有 pdata。