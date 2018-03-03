---
title: "編譯器控制的 LINK 選項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc899fc7f1fc8c1805648e72e14ef13853841c90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options
CL 編譯器會自動呼叫連結，除非您指定 /c 選項。 CL 提供某些控制連結器，透過命令列選項和引數。 下表摘要說明 CL 影響連結的功能。  
  
|CL 規格|CL 動作會影響連結|  
|----------------------|---------------------------------|  
|.C、.cxx、.cpp 或.def 以外的任何檔案名稱副檔名|傳遞做為連結的輸入檔案名稱|  
|*檔名*.def|傳遞 /DEF:*filename*.def|  
|/F*數目*|階段 /STACK:*數目*|  
|/Fd*檔名*|傳遞 /PDB:*檔名*|  
|/Fe*檔名*|傳遞 /out:*檔名*|  
|/Fm*檔名*|階段 /MAP:*檔名*|  
|/Gy|建立封裝函式 (Comdat);啟用函式階層連結|  
|/LD|傳遞 /DLL|  
|/LDd|傳遞 /DLL|  
|/link|將命令列的其餘部分傳遞至連結|  
|/MD 或 /MT|.Obj 檔中將預設程式庫名稱|  
|/Mdd 或 /MTd|.Obj 檔中將預設程式庫名稱。 定義符號**_DEBUG**|  
|/nologo|傳遞 /NOLOGO|  
|/Zd|傳遞 /DEBUG|  
|/Zi 或 /Z7|傳遞 /DEBUG|  
|/Zl|省略預設程式庫名稱，從.obj 檔案|  
  
 如需詳細資訊，請參閱[編譯器選項](../../build/reference/compiler-options.md)。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)