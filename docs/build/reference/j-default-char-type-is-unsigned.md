---
title: "-J (預設 char 類型為 unsigned) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs: C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a49220bf5ee4d990096140f4b2139992b03ad95
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="j-default-char-type-is-unsigned"></a>/J (預設 char 類型為 unsigned)
將預設 `char` 類型從 `signed char` 變更為 `unsigned char`，而且 `char` 類型在擴展為 `int` 類型時，是以零擴充的。  
  
## <a name="syntax"></a>語法  
  
```  
/J  
```  
  
## <a name="remarks"></a>備註  
 如果`char`值明確宣告為`signed`、 **/J**選項不會影響，且值為帶正負號擴充時擴展為`int`型別。  
  
 **/J**選項定義`_CHAR_UNSIGNED`，能在`#ifndef`LIMITS.h 檔案以定義預設值的範圍中`char`型別。  
  
 ANSI C 和 c + + 不需要的特定實作`char`型別。 這個選項適合，當您使用的字元資料，最後將會翻譯成英文以外的語言。  
  
> [!NOTE]
>  如果您搭配 ATL/MFC 使用這個編譯器選項，可能會產生錯誤。 雖然您可以透過定義 `_ATL_ALLOW_CHAR_UNSIGNED` 停用這個錯誤，這個解決方法卻不支援而且未必可行。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。  
  
2.  在專案中**屬性頁**對話方塊中的，在左窗格中**組態屬性**，依序展開**C/c + +** ，然後選取 **命令列**.  
  
3.  在**其他選項** 窗格中，指定**/J**編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)