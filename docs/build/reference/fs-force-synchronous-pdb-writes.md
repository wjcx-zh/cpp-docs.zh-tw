---
title: "-FS （強制同步 PDB 寫入） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /FS
dev_langs:
- C++
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cec8aa3d1b3417b6bfcb35757ac4a4a51961e16b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (強制同步 PDB 寫入)
強制寫入要程式資料庫 (PDB) 檔案，建立[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)或[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)— 透過 MSPDBSRV 序列化。EXE。  
  
## <a name="syntax"></a>語法  
  
```  
/FS  
```  
  
## <a name="remarks"></a>備註  
 根據預設，當**/Zi**或**/ZI**指定，則編譯器會鎖定 PDB 檔案寫入類型資訊和符號偵錯資訊。 當類型數目很大時，這可以大幅降低編譯器產生類型資訊所需的時間。 如果另一個處理序暫時鎖定 PDB 檔案 (例如，防毒程式)，編譯器寫入可能會失敗，而且可能會發生嚴重錯誤。 當 cl.exe 的多個複本存取同一個 PDB 檔，這個問題也可能會發生，例如，如果方案有使用相同中繼目錄的獨立專案或者輸出目錄和平行組建已啟用。 **/FS**編譯器選項防止編譯器鎖定 PDB 檔案，並強制寫入通過 MSPDBSRV。EXE，將序列化存取權。 這可能會使建置時間明顯更久，而且不能避免 cl.exe 的多個執行個體同時存取 PDB 檔案可能發生的所有錯誤。 建議您變更方案，以便獨立專案寫入個別的中繼和輸出位置，或者讓一個專案相依於另一個專案，以強制序列化的專案建置。  
  
 [/MP](../../build/reference/mp-build-with-multiple-processes.md)選項可讓**/FS**預設。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  修改**其他選項**屬性，以包括`/FS`，然後選擇 **確定**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)