---
title: -/vmb、 /vmg （表示方法） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vmb
- /vmg
dev_langs:
- C++
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5263b6c7ca227a10b34c32e0b0801eeddf07b9cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377179"
---
# <a name="vmb-vmg-representation-method"></a>/vmb、/vmg (表示方法)
選取的方法，供編譯器用來表示類別成員的指標。  
  
 使用 **/vmb**如果您一定是之前定義類別成員的類別中宣告的指標。  
  
 使用 **/vmg**至之前定義類別宣告類別成員的指標。 如果您在定義中互相參考的兩個不同類別的成員，可能會發生這項需求。 這類相互參考的類別定義之前必須參考一個類別。  
  
## <a name="syntax"></a>語法  
  
```  
/vmb  
/vmg  
```  
  
## <a name="remarks"></a>備註  
 您也可以使用[pointers_to_members](../../preprocessor/pointers-to-members.md)或[繼承關鍵字](../../cpp/inheritance-keywords.md)在您的程式碼，以指定的指標表示法。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)