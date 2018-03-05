---
title: "虛設常式 （MS-DOS Stub 檔名稱） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2bb7d1b9f56e7cea5d476d5ece6bdfab50fbe7a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (MS-DOS Stub 檔名)
```  
/STUB:filename  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *filename*  
 MS-DOS 應用程式。  
  
## <a name="remarks"></a>備註  
 /STUB 選項會將 MS-DOS stub 程式附加至 Win32 程式。  
  
 會執行檔案中 MS-DOS stub 程式被叫用。 它通常會顯示適當的訊息。不過，任何有效的 MS-DOS 應用程式可以是虛設常式程式。  
  
 指定*filename*虛設常式程式命令列上的冒號 （:） 之後。 這個連結器會檢查*filename*並發出錯誤訊息，如果檔案不是可執行檔。 該程式必須是.exe 檔案。無效的 stub 程式.com 檔案。  
  
 如果未使用此選項，連結器會將發出下列訊息的預設 stub 程式附加：  
  
```  
This program cannot be run in MS-DOS mode.  
```  
  
 建立虛擬裝置驅動程式時*filename*可讓使用者指定檔案名稱包含 （定義於 WINNT IMAGE_DOS_HEADER 結構。H) 以用於 VXD，而不是預設的標題。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)