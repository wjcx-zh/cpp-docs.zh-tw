---
title: "編譯器和連結器中的 Unicode 支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs: C++
helpviewer_keywords: Unicode, Visual C++
ms.assetid: acc1d322-56b9-4696-a30e-2af891a4e288
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 15fefc4cc44edfd67bd8ba89ab68c6965c8639a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>編譯器和連結器中的 Unicode 支援
本主題說明 Visual c + + 建置工具中的 Unicode 支援。  
  
 檔案名稱  
 在命令列上或編譯器指示詞指定的檔名 (例如 #include) 現在可能會包含 Unicode 字元。  
  
 原始程式檔  
 在識別項、 巨集、 字串和字元常值和註解現在支援 Unicode 字元。  現在也支援通用字元名稱。  
  
 Unicode 可以輸入下列編碼中的原始程式碼檔：  
  
-   Utf-16 很少位元組由小到大位元組順序標示 (BOM) 不論  
  
-   使用或不具有 BOM utf-16 big endian  
  
-   Utf-8 有 BOM  
  
 輸出  
 在編譯期間，編譯器會輸出診斷，以 utf-16 主控台。  在您的主控台可顯示的字元取決於主控台視窗的內容。  編譯器輸出重新導向至檔案是以目前的 ANSI 主控台字碼頁。  
  
 連結器回應檔和。DEF 檔案  
 回應檔案和.DEF 檔可以是任一個 utf-16 位元組順序標記或 ANSI。  先前只有 ANSI 支援。  
  
 .asm 和.cod 傾印  
 .asm 和.cod 傾印的 ANSI 預設了與 MASM 的相容性。  您可以使用 /FAu 輸出 utf-8。  請注意，如果您指定 /FAs，混合的原始程式碼會直接列印可能看起來亂碼，例如，如果原始碼為 utf-8，而且您並未指定 /fasu 時。  
  
 您可以啟用在開發環境中的 Unicode 檔案名稱 (請參閱[使用專案屬性](../../ide/working-with-project-properties.md))，請選取適當的工具，然後選取**啟用 Unicode 回應檔**屬性，預設會啟用它。 您可能會變更此預設值的其中一個原因是如果您修改您的開發環境使用的編譯器，並沒有支援的 Unicode。  
  
## <a name="see-also"></a>另請參閱  
 [在命令列上建置 C/c + + 程式碼](../../build/building-on-the-command-line.md)