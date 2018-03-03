---
title: "-MANIFESTDEPENDENCY （指定資訊清單相依性） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
dev_langs:
- C++
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01da83a57769dbe5b86c5bc2a73875231b769cdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (指定資訊清單相依性)
```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## <a name="remarks"></a>備註  
 /MANIFESTDEPENDENCY 可讓您指定屬性，將會放置於\<相依性 > 一節的資訊清單檔案。  
  
 請參閱[/MANIFEST （建立為並存組件資訊清單）](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)如需有關如何建立資訊清單檔案資訊。  
  
 如需有關\<相依性 > 一節的資訊清單檔案，請參閱[發行者組態檔](http://msdn.microsoft.com/library/aa375682)。  
  
 /MANIFESTDEPENDENCY 資訊可以在傳遞至連結器中有兩種：  
  
-   直接在命令列上 （或在回應檔中） 與 /MANIFESTDEPENDENCY。  
  
-   透過[註解](../../preprocessor/comment-c-cpp.md)pragma。  
  
 下列範例示範 /MANIFESTDEPENDENCY 註解 pragma，透過傳遞  
  
```  
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")  
```  
  
 這會產生資訊清單檔中的下列項目：  
  
```  
<dependency>  
  <dependentAssembly>  
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />  
  </dependentAssembly>  
</dependency>  
```  
  
 相同 /MANIFESTDEPENDENCY 註解可以傳遞在命令列，如下所示：  
  
```  
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"  
```  
  
 連結器會收集 /MANIFESTDEPENDENCY 註解、 排除重複的項目，並將產生的 XML 字串新增到資訊清單檔案。  如果連結器找到衝突的項目，資訊清單檔將變成損毀，而且應用程式將無法啟動 （項目可能加入至事件記錄檔，表示失敗的來源）。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**資訊清單檔案**屬性頁。  
  
5.  修改**資訊清單的其他相依性**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)