---
title: "預先定義的規則 | Microsoft Docs"
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
  - "規則，預先定義的"
  - "NMAKE 程式，預先定義的規則"
  - "轉換格式"
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 預先定義的規則
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

預先定義的介面規則會使用 NMAKE 提供的命令和選項巨集。  
  
|規則|命令|預設<br /><br /> 動作|批次<br /><br /> 規則|執行 Nmake 的平台|  
|--------|--------|---------------|---------------|------------------|  
|.asm.exe|$\(AS\) $\(AFLAGS\) $\<|ml $\<|no|x86|  
|.asm.obj|$\(AS\) $\(AFLAGS\) \/c $\<|ml \/c $\<|yes|x86|  
|.asm.exe|$\(AS\) $\(AFLAGS\) $\<|ml64 $\<|no|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|.asm.obj|$\(AS\) $\(AFLAGS\) \/c $\<|ml64 \/c $\<|yes|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|.c.exe|$\(CC\) $\(CFLAGS\) $\<|cl $\<|no|全部|  
|.c.obj|$\(CC\) $\(CFLAGS\) \/c $\<|cl \/c $\<|yes|全部|  
|.cc.exe|$\(CC\) $\(CFLAGS\) $\<|cl $\<|no|全部|  
|.cc.obj|$\(CC\) $\(CFLAGS\) \/c $\<|cl \/c $\<|yes|全部|  
|.cpp.exe|$\(CPP\) $\(CPPFLAGS\) $\<|cl $\<|no|全部|  
|.cpp.obj|$\(CPP\) $\(CPPFLAGS\) \/c $\<|cl \/c $\<|yes|全部|  
|.cxx.exe|$\(CXX\) $\(CXXFLAGS\) $\<|cl $\<|no|全部|  
|.cxx.obj|$\(CXX\) $\(CXXFLAGS\) \/c $\<|cl \/c $\<|yes|全部|  
|.rc.res|$\(RC\) $\(RFLAGS\) \/r $\<|rc \/r $\<|no|全部|  
  
## 請參閱  
 [推斷規則](../build/inference-rules.md)