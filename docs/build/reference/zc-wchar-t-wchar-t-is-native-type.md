---
title: "-Zc: wchar_t （wchar_t 是原生類型） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs: C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3375e39120fdc8f2b0d8d5502aa6def997511ff5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t 是原生類型)
根據 C++ 標準將 `wchar_t` 解析為內建類型。 根據預設， **/zc: wchar_t**上。  
  
## <a name="syntax"></a>語法  
  
```  
/Zc:wchar_t[-]  
```  
  
## <a name="remarks"></a>備註  
 如果**/zc: wchar_t**已開啟，`wchar_t`會對應至 Microsoft 特定原生類型`__wchar_t`。 如果**/Zc:wchar_t-** （以負號） 指定，則`wchar_t`對應至`typedef`如`unsigned short`。 (在 Visual C++ 6.0 和之前版本中，`wchar_t` 並未實作為內建類型，而是在 wchar.h 中宣告為 `typedef` 的 `unsigned short`)。我們不建議**/Zc:wchar_t-**因為 c + + 標準要求`wchar_t`是內建型別。 使用 `typedef` 版本可能會造成可攜性問題。 如果您從舊版的 Visual c + + 升級，並發生編譯器錯誤[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)因為程式碼會嘗試隱含地轉換`wchar_t`至`unsigned short`，我們建議您變更程式碼來修正錯誤，而是設定的**/Zc:wchar_t-**。  
  
 Microsoft 將 `wchar_t` 實作為二位元的不帶正負號值。 如需有關`wchar_t`，請參閱[資料類型範圍](../../cpp/data-type-ranges.md)和[基本類型](../../cpp/fundamental-types-cpp.md)。  
  
 如果您撰寫新程式碼必須仍會使用的舊版程式碼交互操作`typedef`版本`wchar_t`，您可以提供多載兩個`unsigned short`和`__wchar_t`變化`wchar_t`，如此一來，您的程式碼可以連結到使用程式碼編譯**/zc: wchar_t**或將它不會編譯程式碼。 否則，您必須提供兩個不同的程式庫組建，一個使用，一個不含**/zc: wchar_t**啟用。 縱使在這種情況，我們仍然建議您以編譯新程式碼所使用的相同編譯器建置較舊的程式碼。 切勿混合不同編譯器所編譯的二進位檔。  
  
 當**/zc: wchar_t**指定，則**_WCHAR_T_DEFINED**和**_NATIVE_WCHAR_T_DEFINED**符號定義。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。  
  
 如果您的程式碼使用編譯器 COM 全域函式，由於**/zc: wchar_t**現在根據預設，我們建議您將對 comsupp.lib 的明確參考[註解 pragma](../../preprocessor/comment-c-cpp.md)或命令行 — 為 comsuppw.lib 或 comsuppwd.lib。 (如果您必須編譯**/Zc:wchar_t-**，使用 comsupp.lib。)如果您包含 comdef.h 標頭檔，則會為您指定正確的程式庫。 如需編譯器 COM 支援資訊，請參閱[編譯器 COM 支援](../../cpp/compiler-com-support.md)。  
  
 當您編譯 C 程式碼時，不會支援 `wchar_t` 類型。 如需 Visual c + + 一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，依序展開**組態屬性**， **C/c + +**，然後選取**語言**。  
  
3.  修改**將 wchar_t 當做 Built-in 類型**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>。  
  
## <a name="see-also"></a>請參閱  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)