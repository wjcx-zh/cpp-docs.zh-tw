---
title: "連結器工具警告 LNK4227 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4227"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4227"
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 連結器工具警告 LNK4227
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

中繼資料作業警告 \(HRESULT\)：warning\_message  
  
 連結器在合併時偵測到中繼資料有差異：  
  
-   一或多個被參考的組件，含目前正在建置的組件。  
  
-   編譯中有一或多個原始程式檔。  
  
 例如，如果您有相同名稱的兩個全域函式，但所宣告的參數資訊不同 \(宣告不是在所有編譯中都一致\)，可能就會造成 LNK4227 錯誤。  在每一個 .obj 檔上使用 ildasm.exe \/TEXT \/METADATA `object_file`，您就可以看到型別的差異。  
  
 LNK4227 也會報告因其他工具而產生的問題。  例如 al.exe；請參閱 [Al.exe 工具錯誤和警告](http://msdn.microsoft.com/zh-tw/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)。  
  
 中繼資料問題必須先修復才能解決這個警告。  
  
 例如，當被參考組件的簽章方式，不同於參考它的組件之簽章方式時，便會產生 LNK4227。  
  
 下列範例會產生 LNK4227：  
  
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
  
 下列範例會產生 LNK4227：  
  
```  
// LNK4227c.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 然後，  
  
```  
// LNK4227d.cpp  
// compile with: /clr:oldSyntax LNK4227c.cpp /FeLNK4227d.exe  
#using <mscorlib.dll>  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
  
__gc class MyClass  
{  
};  
```  
  
 傳遞了錯誤格式的版本號碼給組件屬性，也可能會產生 LNK4227。'\*' 標記法是 AssemblyVersionAttribute 專用的。若要解除這項警告，除了 AssemblyVersionAttribute 以外，只使用版本屬性中的號碼。  
  
 下列範例會產生 LNK4227：  
  
```  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```