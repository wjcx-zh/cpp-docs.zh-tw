---
title: -Od （停用 （偵錯）） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /od
dev_langs:
- C++
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e287a9991f8192f16ec2f93e4068dc797ff72a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="od-disable-debug"></a>/Od (停用 (偵錯))
會關閉在程式中的所有最佳化，並加速進行編譯。  
  
## <a name="syntax"></a>語法  
  
```  
/Od  
```  
  
## <a name="remarks"></a>備註  
 這個選項是預設值。 因為 **/Od**隱藏程式碼移動，它可簡化偵錯的程序。 如需偵錯編譯器選項的詳細資訊，請參閱[/Z7、 /Zi、 /ZI （偵錯資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**最佳化**屬性頁。  
  
4.  修改**最佳化**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [/Z7、/Zi、/ZI (偵錯資訊格式)](../../build/reference/z7-zi-zi-debug-information-format.md)