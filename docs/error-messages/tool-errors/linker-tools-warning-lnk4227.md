---
title: "連結器工具警告 LNK4227 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ee566318c7d19159f9a2c084d348b5010a65e2de
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-warning-lnk4227"></a>連結器工具警告 LNK4227
中繼資料作業警告 (HRESULT): warning_message  
  
合併時，連結器偵測到中繼資料的差異︰  
  
-   一或多個參考的組件與目前正在建置的組件。  
  
-   一或多個原始程式碼檔編譯中。  
  
例如，LNK4227 可能造成如果您有兩個具有相同名稱但不同宣告的參數資訊的全域函式 （宣告不一致，在所有編譯中）。 使用 ildasm.exe /TEXT /METADATA`object_file`上每個.obj 檔案，您應該會看到類型有何不同。  
  
LNK4227 也會報告而另一種工具所產生的問題。 例如，al.exe;請參閱[Al.exe 工具錯誤和警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)。  
  
中繼資料問題必須固定為解決這個警告。  
  
例如，參考的組件簽署方式不同於參考它的組件時，會產生 LNK4227。  
  
下列範例會產生 LNK4227:  
  
```  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 然後，  
  
```  
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
  
格式錯誤的版本號碼傳遞給組件屬性時，也可能會產生 LNK4227。  ' *' 表示法是非負數特定 assemblyversionattribute 標記組件。  若要解決這個警告，使用數字以外 assemblyversionattribute 標記組件的版本屬性中。  
  
下列範例會產生 LNK4227:  
  
```  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```
