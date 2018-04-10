---
title: 版本 （版本資訊） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
dev_langs:
- C++
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aeb8d2845c5e8daa931e354b149fc1c35b37fbd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="version-version-information"></a>/VERSION (版本資訊)
```  
/VERSION:major[.minor]  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *主要*和*次要*  
 您想要的.exe 或.dll 檔的標頭中的版本號碼。  
  
## <a name="remarks"></a>備註  
 /VERSION 選項會告訴連結器將版本號碼放.exe 或.dll 檔案的標頭中。 使用 DUMPBIN [/HEADERS](../../build/reference/headers.md)以查看映像版本欄位，選擇性標頭值，以檢視 /VERSION 的效果。  
  
 *主要*和*次要*引數是 0 到 65535 的範圍中的十進位數字。 預設值為 0.0 版。  
  
 以 /VERSION 指定的資訊不會影響您在檔案總管中檢視應用程式屬性時所顯示的版本資訊。 這些版本資訊來自於用來建置應用程式的資源檔案。 請參閱[版本資訊編輯器](../../windows/version-information-editor.md)如需詳細資訊。  
  
 若要插入的版本號碼的另一個方法是使用[版本](../../build/reference/version-c-cpp.md)模組定義陳述式。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**一般**屬性頁。  
  
4.  修改**版本**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)