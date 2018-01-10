---
title: "-Zp （結構成員對齊） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
dev_langs: C++
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d387e0ab020e96afb3e2975b5c8686b668cbc10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="zp-struct-member-alignment"></a>/Zp (結構成員對齊)
控制結構的成員會封裝為記憶體的方式，並指定在模組中的所有結構相同的封裝。  
  
## <a name="syntax"></a>語法  
  
```  
/Zp[1|2|4|8|16]  
```  
  
## <a name="remarks"></a>備註  
 當您指定這個選項時，每個結構成員之後第一個儲存於成員類型的大小或`n`-位元組界限 (其中`n`是 1、 2、 4、 8 或 16)，兩者中較小。  
  
 下表說明可用的值。  
  
 1  
 1 位元組界限上封裝結構。 與相同**/Zp**。  
  
 2  
 2 位元組界限上封裝結構。  
  
 4  
 4 位元組界限上封裝結構。  
  
 8  
 （預設值） 的 8 位元組界限上封裝結構。  
  
 16  
 16 位元組界限上封裝結構。  
  
 除非您有特定的對齊需求，您不應該使用此選項。  
  
 您也可以使用[套件](../../preprocessor/pack.md)來控制結構封裝。 如需對齊的詳細資訊，請參閱：  
  
-   [align](../../cpp/align-cpp.md)  
  
-   [__alignof 運算子](../../cpp/alignof-operator.md)  
  
-   [__unaligned](../../cpp/unaligned.md)  
  
-   [結構對齊範例](../../build/examples-of-structure-alignment.md)(x64 專用)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**程式碼產生**屬性頁。  
  
4.  修改**結構成員對齊**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)