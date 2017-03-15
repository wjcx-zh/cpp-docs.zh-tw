---
title: "/MD、/MT、/LD (使用執行階段程式庫) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ld"
  - "/mt"
  - "VC.Project.VCCLWCECompilerTool.RuntimeLibrary"
  - "VC.Project.VCCLCompilerTool.RuntimeLibrary"
  - "/md"
  - "/ml"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LD 編譯器選項 [C++]"
  - "/MD 編譯器選項 [C++]"
  - "/MDd 編譯器選項 [C++]"
  - "/MT 編譯器選項 [C++]"
  - "/MTd 編譯器選項 [C++]"
  - "_STATIC_CPPLIB 符號"
  - "DLL [C++], 編譯器選項"
  - "LD 編譯器選項 [C++]"
  - "-LD 編譯器選項 [C++]"
  - "LIBC.lib"
  - "LIBCD.lib"
  - "LIBCMT.lib"
  - "LIBCMTD.lib"
  - "MD 編譯器選項 [C++]"
  - "-MD 編譯器選項 [C++]"
  - "MDd 編譯器選項 [C++]"
  - "-MDd 編譯器選項 [C++]"
  - "MSVCRT.lib"
  - "MSVCRTD.lib"
  - "MT 編譯器選項 [C++]"
  - "-MT 編譯器選項 [C++]"
  - "MTd 編譯器選項 [C++]"
  - "-MTd 編譯器選項 [C++]"
  - "multithread 編譯器選項"
  - "執行緒 [C++], multithread 編譯器選項"
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# /MD、/MT、/LD (使用執行階段程式庫)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指出多執行緒模組是否為 DLL，並指定執行階段程式庫的正式版本或偵錯版本。  
  
## 語法  
  
```  
/MD[d]  
/MT[d]  
/LD[d]  
```  
  
## 備註  
  
|選項|描述|  
|--------|--------|  
|**\/MD**|讓應用程式使用多執行緒特定與 DLL 特定版本的執行階段程式庫。  定義 `_MT` 和 `_DLL`，並讓編譯器將程式庫名稱 MSVCRT.lib 放入 .obj 檔。<br /><br /> 使用這個選項編譯的應用程式，都以靜態方式連結至 MSVCRT.lib。  此程式庫提供可讓連結器解析外部參考的程式碼層。  實際的工作程式碼包含在 MSVCR*versionnumber*.DLL 中，它在執行階段時必須能提供與 MSVCRT.lib 連結的應用程式使用。|  
|**\/MDd**|定義 `_DEBUG`、`_MT` 和 `_DLL`，並讓應用程式使用偵錯多執行緒特定與 DLL 特定版本的執行階段程式庫。  它也會讓編譯器將程式庫名稱 MSVCRTD.lib 放入 .obj 檔中。|  
|**\/MT**|讓應用程式使用多執行緒、靜態版本的執行階段程式庫。  定義 `_MT`，並讓編譯器將程式庫名稱 LIBCMT.lib 置入 .obj 檔案中，讓連結器能夠使用 LIBCMT.lib 解析外部符號。|  
|**\/MTd**|定義 `_DEBUG` 和 `_MT`。  這個選項也會讓編譯器將程式庫名稱 LIBCMTD.lib 放入 .obj 檔中，使連結器可以使用 LIBCMTD.lib 解析外部符號。|  
|**\/LD**|建立 DLL。<br /><br /> 傳遞 **\/DLL** 選項給連結器。  連結器會尋找 \(並非必要\) `DllMain` 函式。  如果您沒有撰寫 `DllMain` 函式，連結器將會插入一個會傳回 TRUE 的 `DllMain` 函式。<br /><br /> 連結 DLL 啟始程式碼。<br /><br /> 如果在命令列上未指定匯出 \(.exp\) 檔案，則會建立匯入程式庫 \(.lib\)。  您應將匯入程式庫連結至呼叫 DLL 的應用程式。<br /><br /> 將 [\/Fe \(命名 EXE 檔案\)](../../build/reference/fe-name-exe-file.md) 解讀為命名 DLL 而不是 .exe 檔。  根據預設，程式名稱會變成 *basename*.dll 而不是 *basename*.exe。<br /><br /> 除非您明確指定 **\/MD**，否則皆會隱含 **\/MT**。|  
|**\/LDd**|建立偵錯 DLL。  定義 `_MT` 和 `_DEBUG`。|  
  
 如需有關 C 執行階段程式庫和以 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 編譯時所使用程式庫的詳細資訊，請參閱 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
 傳遞至指定連結器之引動過程的所有模組，都必須以相同執行階段程式庫編譯器選項 \(**\/MD**、**\/MT**、**\/LD**\) 進行編譯。  
  
 如需如何使用偵錯版本執行階段程式庫的詳細資訊，請參閱 [C 執行階段程式庫參考](../../c-runtime-library/c-run-time-library-reference.md)。  
  
 知識庫文件 Q140584 中也有關於如何選擇適當 C 執行階段程式庫的討論。  
  
 如需 DLL 的詳細資訊，請參閱 [Visual C\+\+ 中的 DLL](../../build/dlls-in-visual-cpp.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**程式碼產生**\] 屬性頁。  
  
4.  修改 \[**執行階段程式庫**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)