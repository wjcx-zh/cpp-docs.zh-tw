---
title: "-Zc: strictStrings （停用字串常值型別轉換） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:strictStrings
- strictStrings
dev_langs:
- C++
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f316c5fc9209f968219d770a15e6576880b69954
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (停用字串常值型別轉換)
指定時，對於使用字串常值初始的指標，編譯器需要嚴格的 `const` 限定一致性。  
  
## <a name="syntax"></a>語法  
  
```  
/Zc:strictStrings[-]  
```  
  
## <a name="remarks"></a>備註  
 如果**/zc: strictstrings**指定，則編譯器會強制使用 standard c + +`const`限定性條件字串常值，做為類型 '陣列`const char`' 或 ' 陣列`const wchar_t`'，取決於宣告。 字串常值不可變，如果嘗試修改其內容，則會導致執行階段存取違規錯誤。 您必須將字串指標宣告為 `const`，以使用字串常值來對其進行初始化，或者使用明確的 `const_cast`，對非 `const` 指標進行初始化。 根據預設，或者如果**/Zc:strictStrings-**指定，則編譯器不會強制執行標準 c + +`const`使用字串常值初始化的字串指標的資格。  
  
 使用**/zc: strictstrings**選項，可以防止編譯不正確的程式碼。 此範例顯示簡單的宣告錯誤如何導致執行階段損毀：  
  
```cpp  
// strictStrings_off.cpp  
// compile by using: cl /W4 strictStrings_off.cpp  
int main() {  
   wchar_t* str = L"hello";  
   str[2] = L'a'; // run-time error: access violation  
}  
```  
  
 當**/zc: strictstrings**已啟用，相同的程式碼會報告錯誤的宣告中`str`。  
  
```cpp  
// strictStrings_on.cpp  
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp  
int main() {  
   wchar_t* str = L"hello"; // error: Conversion from string literal   
   // loses const qualifier  
   str[2] = L'a';   
}  
```  
  
 如果您使用 `auto`，來宣告字串指標，則編譯器會為您建立正確的 `const` 指標類型宣告。 如果嘗試修改 `const` 指標的內容，則編譯器會報告錯誤。  
  
> [!NOTE]
>  中的 c + + 標準程式庫[!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)]不支援**/zc: strictstrings**編譯器選項，在偵錯組建。 如果您看到數個[C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md)您在建置中的錯誤輸出，這可能是原因。  
  
 如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  修改**其他選項**屬性，以包括`/Zc:strictStrings`，然後選擇 **確定**。  
  
## <a name="see-also"></a>請參閱  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)