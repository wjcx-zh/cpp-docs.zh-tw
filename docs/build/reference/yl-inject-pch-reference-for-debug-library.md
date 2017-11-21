---
title: "-Yl （插入偵錯程式庫的 PCH 參考） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yi
dev_langs: C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 271681849d78eb8a6a4032bcbafbcc81b96c9f9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (插入偵錯程式庫的 PCH 參考)
如果建立偵錯的程式庫使用先行編譯標頭和組建失敗時，使用。  
  
## <a name="syntax"></a>語法  
  
```  
/Ylsymbol  
```  
  
```  
/Yl-  
```  
  
## <a name="arguments"></a>引數  
 `symbol`  
 要儲存在物件模組中的任意符號。  
  
 \-  
 減號 （-） 明確停用**/Yl**編譯器選項。  
  
## <a name="remarks"></a>備註  
 根據預設，編譯器會使用**/Yl**選項 (而不指定*符號*)。 **/Yl**選項可讓偵錯工具取得類型的完整資訊。 **/Yl-**停用的預設行為。  
  
 當您編譯同名的模組**/Yc**和**/Yl**`symbol`，編譯器會建立一個符號 __ @ 類似@_PchSym\_@00@..。 @`symbol`，其中的省略符號 （...） 代表連結器產生的字元字串，並將它儲存在物件模組中。 指定的符號，這會導致連結器包含此物件模組和程式庫的偵錯資訊是指您此先行編譯標頭使用編譯任何原始程式檔。  
  
 您可以使用這個選項，來產生 LNK1211。 當您指定[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)和[/Z7、 /Zi、 /ZI （偵錯資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md)選項，編譯器會建立包含偵錯資訊的先行編譯標頭檔。 當您儲存文件庫，來建立物件模組和原始碼程式庫並不是指任何函式的先行編譯標頭檔會定義的使用中的先行編譯標頭時，就可能發生錯誤。  
  
 若要解決此問題，請指定**/Yl**`symbol`，其中`symbol`是任意符號的程式庫的名稱，當您建立不包含任何函式定義的先行編譯標頭檔。 此選項會指示編譯器將偵錯資訊儲存在先行編譯標頭檔中。  
  
 如需先行編譯標頭的詳細資訊，請參閱：  
  
-   [/Y （先行編譯標頭）](../../build/reference/y-precompiled-headers.md)  
  
-   [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)  
  
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