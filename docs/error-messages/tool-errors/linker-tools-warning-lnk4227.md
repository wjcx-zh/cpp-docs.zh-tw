---
title: 連結器工具警告 LNK4227 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b56617ee355654dfbb198252ea37cdb344950cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4227"></a>連結器工具警告 LNK4227  
  
> 中繼資料作業警告 (*HRESULT*): *warning_message*  
  
合併時，連結器偵測到中繼資料的差異：  
  
-   一或多個參考的組件與目前正在建置組件。  
  
-   一或多個原始程式碼檔編譯中。  
  
例如，LNK4227 可能因為如果您有兩個具有相同名稱但不同宣告的參數資訊的全域函式 （也就是宣告不是在所有編譯中一致）。 使用 ildasm.exe /TEXT /METADATA *object_file*上每個.obj 檔案，以查看 型別有何不同。  
  
LNK4227 也用於由另一個工具產生的報告問題。 搜尋警告訊息，如需詳細資訊。  
  
中繼資料的問題必須固定為解決這個警告。  
  
## <a name="example"></a>範例  
  
參考的組件以不同方式比在參考的組件簽署時，會產生 LNK4227。  
  
下列範例會產生 LNK4227:  
  
```cpp  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 然後，  
  
```cpp  
// LNK4227b.cpp  
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
// Try the following line instead  
// [assembly:AssemblyDelaySignAttribute(false)];  
  
ref class MyClass  
{  
};  
```  
  
## <a name="example"></a>範例  
  
錯誤格式的版本號碼會傳遞至組件屬性時，也可能會產生 LNK4227。  ' *' 表示法是非負數特有`AssemblyVersionAttribute`。  若要解決這個警告，使用僅使用數字中的版本屬性以外`AssemblyVersionAttribute`。  
  
下列範例會產生 LNK4227:  
  
```cpp  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```