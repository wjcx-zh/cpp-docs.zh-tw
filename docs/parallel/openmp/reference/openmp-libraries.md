---
title: "OpenMP Libraries | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# OpenMP Libraries
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

討論 OpenMP run\-time 程式庫，Visual C\+\+ 所構成的.lib 檔案。  
  
 下列程式庫包含 Visual C\+\+ OpenMP run\-time 程式庫函式。  
  
|OpenMP run\-time 程式庫|特性|  
|--------------------------|--------|  
|VCOMP。LIB|多執行緒的動態連結 \(如 VCOMP 的匯入程式庫。LIB\)。|  
|VCOMPD。LIB|多執行緒的動態連結 \(如 VCOMPD 的匯入程式庫。筆記電腦螢幕\) \(偵錯\)|  
  
 如果編譯中定義了 \_DEBUG，而且`#include omp.h`在原始程式碼中，VCOMPD。LIB 會預設 lib。  否則，VCOMP。將會使用 LIB。  
  
 您可以使用[\/NODEFAULTLIB \(忽略程式庫\)](../../../build/reference/nodefaultlib-ignore-libraries.md)移除預設 lib，並明確地連結與您所選擇的 lib。  
  
 OpenMP Dll 的可轉散發 Visual C\+\+ 目錄中，而且必須使用 OpenMP 應用程式一起散發。  
  
## 請參閱  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)