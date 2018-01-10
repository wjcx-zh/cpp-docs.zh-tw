---
title: "-Fe （命名 EXE 檔案） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /fe
dev_langs: C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 83965ef2bf64f77dbcb1eb9832e7178c30260d16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fe-name-exe-file"></a>/Fe (命名 EXE 檔案)
指定的名稱和.exe 檔或 DLL 編譯器所建立的目錄。  
  
## <a name="syntax"></a>語法  
  
```  
/Fepathname  
```  
  
## <a name="remarks"></a>備註  
 如果沒有這個選項，編譯器會提供檔案的預設名稱，使用命令列的副檔名.exe 或.dll 上指定第一個來源或目的檔的基底名稱。  
  
 如果您指定[/c （編譯而不連結）](../../build/reference/c-compile-without-linking.md)、 編譯而不連結， **/Fe**沒有任何作用。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**一般**屬性頁。  
  
4.  修改**輸出檔**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。  
  
## <a name="example"></a>範例  
 下列命令列編譯和連結目前的目錄中的所有 C 原始程式檔。 產生可執行檔為 PROCESS.exe，並建立 C:\BIN 目錄中。  
  
```  
CL /FeC:\BIN\PROCESS *.C  
```  
  
## <a name="example"></a>範例  
 下列命令列建立可執行檔中的`C:\BIN`具有相同的基底名稱做為第一個來源或物件檔案：  
  
```  
CL /FeC:\BIN\ *.C  
```  
  
## <a name="see-also"></a>請參閱  
 [輸出檔 (/ F) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)