---
title: Platform、 default 和 cli 命名空間 （c + + 元件延伸模組） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- lang
- cli
dev_langs:
- C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c63ce7dc5dcd326de426c4e4738a11e24f93161c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015529"
---
# <a name="platform-default-and-cli-namespaces--c-component-extensions"></a>Platform、default 和 cli 命名空間 (C++ 元件擴充功能)
命名空間會限定語言項目的名稱，因此名稱不會與原始程式碼中其他位置的相同名稱發生衝突。 例如，名稱衝突可能會使編譯器無法辨識[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。 編譯器會使用命名空間，但是命名空間不會保留在編譯的組件中。  
  
## <a name="all-runtimes"></a>所有執行階段  
 當您建立專案時，Visual C++ 會為專案提供預設的命名空間。 雖然 Windows 執行階段中的.winmd 檔案名稱必須符合的根命名空間的名稱，您可以手動命名的命名空間。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 如需詳細資訊，請參閱 <<c0> [ 命名空間和類型可視性 (C + + /CX)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx)。  
  
### <a name="requirements"></a>需求  
 編譯器選項：`/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
### <a name="syntax"></a>語法  
  
```cpp  
using namespace cli;  
```  
  
### <a name="remarks"></a>備註  
  
 C + + /cli CLI 支援**cli**命名空間。 進行編譯時`/clr`，則**使用**隱含的語法區段中的陳述式。  
  
 中有下列語言功能**cli**命名空間：  
  
-   [陣列](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### <a name="requirements"></a>需求  
 編譯器選項：`/clr`  
  
### <a name="examples"></a>範例  
  
 下列程式碼範例示範的是可以使用中的符號**cli**為使用者定義的符號，在您的程式碼中的命名空間。  不過，一旦您這麼做，您必須明確或隱含地限定您參考**cli**相同名稱的語言項目。  
  
```cpp  
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
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)