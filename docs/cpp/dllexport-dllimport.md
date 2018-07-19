---
title: dllexport、 dllimport |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- dllimport_cpp
- dllexport_cpp
dev_langs:
- C++
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a330ecf221d210134425c4bf39c17bac0f5006dc
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940530"
---
# <a name="dllexport-dllimport"></a>dllexport、dllimport
**Microsoft 專屬**  
  
 **Dllexport**並**dllimport**儲存類別屬性是 C 和 c + + 語言的 Microsoft 專有擴充功能。 您可以使用它們在 DLL 中匯出和匯入函式、資料和物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
   __declspec( dllimport ) declarator  
   __declspec( dllexport ) declarator  
```  
  
## <a name="remarks"></a>備註  
 這些屬性明確定義其用戶端的 DLL 介面 (可以是可執行檔或另一個 DLL)。 函式宣告為**dllexport**至少就不需要模組定義 (.def) 檔案，匯出的函式規格。 **Dllexport**屬性會取代 **__export**關鍵字。  
  
 如果類別已標記為 declspec(dllexport)，在類別階層中類別樣板的特製化會隱含標記為 declspec(dllexport)。 這表示類別樣板是明確具現化，必須定義類別的成員。  
  
 **dllexport**函式會公開以其裝飾名稱的函式。 對於 C++ 函式，這包括名稱修飾 (Name Mangling)。 對於 C 函式或宣告為 `extern "C"` 的函式，其中包括根據呼叫慣例的平台專屬裝飾。 C/c + + 程式碼中名稱裝飾的資訊，請參閱[裝飾名稱](../build/reference/decorated-names.md)。 使用 `__cdecl` 呼叫慣例，不會將名稱裝飾套用至已匯出的 C 函式或 C++ `extern "C"` 函式。  
  
 若要匯出未裝飾的名稱，則連結方式是使用在 EXPORTS 區段中定義未裝飾名稱的模組定義 (.def) 檔。 如需詳細資訊，請參閱 <<c0> [ 匯出](../build/reference/exports.md)。 若要匯出未裝飾的名稱的另一種方式是使用`#pragma comment(linker, "/export:alias=decorated_name")`指示詞中的原始程式碼。  
  
 當您宣告**dllexport**或是**dllimport**，您必須使用[擴充屬性語法](../cpp/declspec.md)而 **__declspec**關鍵字。  
  
## <a name="example"></a>範例  
  
```cpp  
// Example of the dllimport and dllexport class attributes  
__declspec( dllimport ) int i;  
__declspec( dllexport ) void func();  
```  
  
 或者，您可以使用巨集定義讓程式碼更容易讀取：  
  
```cpp  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllImport int j;  
DllExport int n;  
```  
  
 如需詳細資訊，請參閱:  
  
-   [定義和宣告](../cpp/definitions-and-declarations-cpp.md)  
  
-   [使用 dllexport 和 dllimport 定義內嵌 C++ 函式](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
-   [一般規則和限制](../cpp/general-rules-and-limitations.md)  
  
-   [在 C++ 類別中使用 dllimport 和 dllexport](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)