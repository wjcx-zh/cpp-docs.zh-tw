---
title: "-Tc、-Tp，-TC、-TP （指定原始程式檔類型） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
dev_langs: C++
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.assetid: 7d9d0a65-338b-427c-8b48-fff30e2f9d2b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69ccd08967d386780744fb85476033430127ba3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc、/Tp、/TC、/TP (指定原始程式檔類型)
**/Tc**選項指定`filename`是 C 原始程式檔，即使它並沒有副檔名為.c。 **/Tp**選項指定`filename`是 c + + 原始程式檔，即使它沒有副檔名為.cpp 或.cxx。 選項之間的空格和`filename`是選擇性的。 每個選項會指定一個檔案。若要指定其他檔案，重複此選項。  
  
 **/TC**和**/TP**全域變化的**/Tc**和**/Tp**。 指定編譯器在處理為 C 原始程式檔名為命令列上的所有檔案 (**/TC**) 或 c + + 原始程式檔 (**/TP**)，而不考慮此選項在命令列上的位置。 這些全域選項可根據單一檔案，藉由覆寫**/Tc**或**/Tp**。  
  
## <a name="syntax"></a>語法  
  
```  
/Tcfilename  
/Tpfilename  
/TC  
/TP  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 C 或 c + + 原始程式檔。  
  
## <a name="remarks"></a>備註  
 根據預設，CL 會假設副檔名為.c 檔案是 C 原始程式檔，而具有.cpp 或.cxx 副檔名的檔案是 c + + 原始程式檔。  
  
 當任一**TC**或**Tc**指定選項的任何規格[/zc: wchar_t （wchar_t 是原生類型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)選項會被忽略。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**進階**屬性頁。  
  
4.  修改**編譯為**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>。  
  
## <a name="examples"></a>範例  
 下列 CL 命令列指定 MAIN.c、 TEST.prg 和 COLLATE.prg 所有 C 原始程式檔。 CL 不會辨識 PRINT.prg。  
  
```  
CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG  
```  
  
 下列 CL 命令列指定 TEST1.c、 TEST2.cxx、 TEST3.huh 和 TEST4.o 會編譯為 c + + 檔案，並 TEST5.z 編譯為 C 檔案。  
  
```  
CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP  
```  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)