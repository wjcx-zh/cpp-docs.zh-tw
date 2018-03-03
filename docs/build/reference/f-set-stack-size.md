---
title: "-F （設定堆疊大小） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /f
dev_langs:
- C++
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b464a4fb28eb83ef0570416d0cb18fd8f965e0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="f-set-stack-size"></a>/F (設定堆疊大小)
設定程式的堆疊大小 （位元組）。  
  
## <a name="syntax"></a>語法  
  
```  
/F number  
```  
  
## <a name="arguments"></a>引數  
 `number`  
 堆疊大小 （位元組）。  
  
## <a name="remarks"></a>備註  
 如果沒有這個選項的堆疊大小預設為 1 MB。 `number`引數可以是以十進位數或 C 語言表示法。 引數的範圍可從 1 至連結器接受的最大堆疊大小。 連結器會無條件進位到最接近的 4 個位元組指定的值。 之間的間距**/F**和`number`是選擇性的。  
  
 您可能需要增加的堆疊大小，如果您的程式取得堆疊溢位 」 訊息。  
  
 您也可以設定堆疊大小：  
  
-   使用**/堆疊**連結器選項。 如需詳細資訊，請參閱[/堆疊](../../build/reference/stack.md)。  
  
-   使用 EDITBIN 的.exe 檔案。 如需詳細資訊，請參閱[EDITBIN 參考](../../build/reference/editbin-reference.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)