---
title: "Platform, default, and cli Namespaces  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "lang"
  - "cli"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lang namespace"
  - "cli namespace"
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Platform, default, and cli Namespaces  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命名空間會限定語言項目的名稱，因此名稱不會與原始程式碼中其他位置的相同名稱發生衝突。  例如，名稱衝突可能會使編譯器無法辨識[視內容而有所區別的關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  編譯器會使用命名空間，但是命名空間不會保留在編譯的組件中。  
  
## 所有執行階段  
 當您建立專案時，Visual C\+\+ 會為專案提供預設的命名空間。  您可以手動將命名空間重新命名，不過在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]中，.winmd 檔案的名稱必須與根命名空間的名稱相符。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 如需詳細資訊，請參閱[命名空間和類型可視性 \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx)。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **語法**  
  
```  
using namespace cli;  
```  
  
 **備註**  
  
 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 支援 `cli` 命名空間。  使用 **\/clr** 進行編譯時，會隱含＜語法＞一節中的 `using` 陳述式。  
  
 `cli` 命名空間中具有下列語言功能：  
  
-   [Arrays](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)  
  
-   [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列程式碼範例將示範可以在 `cli` 命名空間中使用符號做為您程式碼中的使用者定義符號。  不過，一旦這麼做，就必須明確或隱含地限定同名 `cli` 語言項目的參考。  
  
```  
// cli_namespace.cpp  
// compile with: /clr  
using namespace cli;  
int main() {  
   array<int> ^ MyArray = gcnew array<int>(100);  
   int array = 0;  
  
   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062  
  
   // OK  
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);  
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);  
}  
```  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)