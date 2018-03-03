---
title: "-H （限制外部名稱的長度） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /h
dev_langs:
- C++
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5e862eb8e45d1f2558592c0bb54c1adb9305f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="h-restrict-length-of-external-names"></a>/H (限制外部名稱的長度)
已取代。 限制外部名稱的長度。  
  
## <a name="syntax"></a>語法  
  
```  
/Hnumber  
```  
  
## <a name="arguments"></a>引數  
 `number`  
 指定外部名稱在程式中允許的最大長度。  
  
## <a name="remarks"></a>備註  
 根據預設，外部 （公用） 名稱的長度會為 2047 個字元。 這是 C 和 c + + 程式，則為 true。 使用**/H**只能減少識別項的最大容許長度，不會增加它。 之間的空格**/H**和`number`是選擇性的。  
  
 如果程式包含的外部名稱的長度超過`number`，額外的字元會被忽略。 如果您編譯程式時不使用**/H**和識別項包含超過 2047 個字元，編譯器會產生[嚴重錯誤 C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)。  
  
 長度限制包括任何編譯器建立的前置底線 (_) 或 at 符號 (@)。 這些字元是識別項的一部分，而且需要有效的位置。  
  
-   編譯器會將前置底線 (_) 加入至名稱所修改`__cdecl`（預設值） 和`__stdcall`呼叫慣例和前置字元 @ 記號 (@) 名稱來修改`__fastcall`呼叫慣例。  
  
-   編譯器會將引數大小資訊附加至名稱所修改`__fastcall`和`__stdcall`呼叫慣例，並將類型資訊加入至 c + + 名稱。  
  
 您可能會發現**/H**很有用：  
  
-   當您建立混合語言或可攜式程式。  
  
-   當您使用工具，會限制的外部識別項的長度。  
  
-   當您想要限制的符號偵錯組建中使用的空間量。  
  
 下列範例會示範如何使用**/H**實際引發錯誤，如果識別項長度太多限制：  
  
```cpp  
// compiler_option_H.cpp  
// compile with: /H5  
// processor: x86  
// LNK2005 expected  
void func1(void);  
void func2(void);  
  
int main() { func1(); }  
  
void func1(void) {}  
void func2(void) {}  
```  
  
 您也必須小心使用**/H**預先定義的編譯器識別項的選項。 如果識別碼長度上限太小，某些預先定義的識別項將為無法解析，以及特定程式庫函式呼叫。 比方說，如果`printf`使用函式和選項**/H5**指定在編譯時期，符號**_prin**會以參照建立`printf`，，這將會找不到在 程式庫。  
  
 使用**/H**與不相容[/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)。  
  
 **/H**選項已被取代，因為 Visual Studio 2005; 最大長度限制已經增加和**/H**不再需要。 如需已被取代的編譯器選項的清單，請參閱**已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。  
  
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