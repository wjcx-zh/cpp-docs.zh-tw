---
title: "/c (編譯而不連結) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/c"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/c 編譯器選項 [C++]"
  - "c 編譯器選項 [C++]"
  - "-c 編譯器選項 [C++]"
  - "cl.exe 編譯器, 編譯而不連結"
  - "隱藏連結"
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /c (編譯而不連結)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

防止自動呼叫 LINK。  
  
## 語法  
  
```  
/c  
```  
  
## 備註  
 使用 **\/c** 編譯只會建立 .obj 檔案。  您可以用適當的檔案和選項明確地呼叫 LINK 來執行組建的連結階段。  
  
 在開發環境中建立的任何內部專案都是預設為使用 **\/c** 選項。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
-   這個選項在開發環境內無法使用。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   若要用程式設計的方式設定這個編譯器選項，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>。  
  
## 範例  
 以下命令列會建立目的檔 FIRST.obj 和 SECOND.obj，  THIRD.obj 則會被忽略。  
  
```  
CL /c FIRST.C SECOND.C THIRD.OBJ  
```  
  
 若要建立可執行檔，您必須叫用 LINK：  
  
```  
LINK firsti.obj second.obj third.obj /OUT:filename.exe  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)