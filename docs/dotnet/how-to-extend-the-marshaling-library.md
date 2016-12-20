---
title: "如何：擴充封送處理程式庫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "封送處理程式庫, 擴充"
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：擴充封送處理程式庫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題會說明如何擴充封送處理 \(Marshaling\) 程式庫，在資料型別之間提供更多轉換。  使用者可以針對程式庫目前不支援的任何資料轉換，擴充封送處理程式庫。  
  
 您可以用兩種方式之一來擴充封送處理程式庫，也就是使用或不使用 [marshal\_context 類別](../dotnet/marshal-context-class.md)。  請檢閱 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md) 主題，以判斷新的轉換是否需要內容。  
  
 在這兩種情況下，您都會先為新的封送處理轉換建立檔案。  這種做法是為了要保存標準封送處理程式庫檔案的完整性。  如果您要將專案移植到另一部電腦，或是給另一個程式設計人員，都必須一起複製新的封送處理檔案與專案的其餘部分。  這種做法可以保證接收到專案的使用者會收到新的轉換，而且不需要修改任何程式庫檔案。  
  
### 以不需要內容的轉換來擴充封送處理程式庫  
  
1.  建立檔案以儲存新的封送處理函式，例如 MyMarshal.h。  
  
2.  包含一個或多個封送處理程式庫檔案：  
  
    -   儲存基底型別的 marshal.h。  
  
    -   儲存 Windows 資料型別的 marshal\_windows.h。  
  
    -   儲存 STL 資料型別的 marshal\_cppstd.h。  
  
    -   儲存 ATL 資料型別的 marshal\_atl.h。  
  
3.  請在這些步驟的結尾使用此程式碼來撰寫轉換函式。  在這段程式碼中，TO 是要轉換成的型別，FROM 是轉換前的型別，`from` 則是要轉換的參數。  
  
4.  請以程式碼取代有關轉換邏輯的註解，此程式碼可將 `from` 參數轉換成 TO 型別的物件，並傳回已轉換的物件。  
  
```  
namespace msclr {  
   namespace interop {  
      template<>  
      inline TO marshal_as<TO, FROM> (const FROM& from) {  
         // Insert conversion logic here, and return a TO parameter.  
      }  
   }  
}  
```  
  
### 以需要內容的轉換來擴充封送處理程式庫  
  
1.  建立檔案以儲存新的封送處理函式，例如 MyMarshal.h。  
  
2.  包含一個或多個封送處理程式庫檔案：  
  
    -   儲存基底型別的 marshal.h。  
  
    -   儲存 Windows 資料型別的 marshal\_windows.h。  
  
    -   儲存 STL 資料型別的 marshal\_cppstd.h。  
  
    -   儲存 ATL 資料型別的 marshal\_atl.h。  
  
3.  請在這些步驟的結尾使用此程式碼來撰寫轉換函式。  在這段程式碼中，TO 是要轉換成的型別，FROM 是轉換前的型別，`toObject` 是要在其中儲存結果的指標，`fromObject` 則是要轉換的參數。  
  
4.  請以程式碼取代有關初始化的註解，此程式碼可將 `toPtr` 初始化為適當的空值。  例如，如果是指標，便請將其設定為 `NULL`。  
  
5.  請以程式碼取代有關轉換邏輯的註解，此程式碼可將 `from` 參數轉換成 *TO* 型別的物件。  這個轉換後的物件將會儲存在 `toPtr` 中。  
  
6.  請以程式碼取代有關設定 `toObject` 的註解，此程式碼可將 `toObject` 轉換成您的轉換後物件。  
  
7.  請以程式碼取代有關清除原生資源的註解，此程式碼可釋放 `toPtr` 所配置的所有記憶體。  如果 `toPtr` 使用 `new` 來配置記憶體，便請使用 `delete` 來釋放記憶體。  
  
```  
namespace msclr {  
   namespace interop {  
      template<>  
      ref class context_node<TO, FROM> : public context_node_base  
      {  
      private:  
         TO toPtr;  
      public:  
         context_node(TO& toObject, FROM fromObject)  
         {  
            // (Step 4) Initialize toPtr to the appropriate empty value.  
            // (Step 5) Insert conversion logic here.  
            // (Step 6) Set toObject to the converted parameter.  
         }  
         ~context_node()  
         {  
            this->!context_node();  
         }  
      protected:  
         !context_node()  
         {  
            // (Step 7) Clean up native resources.  
         }  
      };  
   }  
}   
```  
  
## 範例  
 下列範例會以不需要內容的轉換來擴充封送處理程式庫。  在此範例中，程式碼會將員工資訊從原生資料型別轉換成 Managed 資料型別。  
  
```  
// MyMarshalNoContext.cpp  
// compile with: /clr  
#include <msclr/marshal.h>  
  
value struct ManagedEmp {  
   System::String^ name;  
   System::String^ address;  
   int zipCode;  
};  
  
struct NativeEmp {  
   char* name;  
   char* address;  
   int zipCode;  
};  
  
namespace msclr {  
   namespace interop {  
      template<>  
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {  
         ManagedEmp^ toValue = gcnew ManagedEmp;  
         toValue->name = marshal_as<System::String^>(from.name);  
         toValue->address = marshal_as<System::String^>(from.address);  
         toValue->zipCode = from.zipCode;  
         return toValue;  
      }  
   }  
}  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {   
   NativeEmp employee;  
  
   employee.name = "Jeff Smith";  
   employee.address = "123 Main Street";  
   employee.zipCode = 98111;  
  
   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);  
  
   Console::WriteLine("Managed name: {0}", result->name);  
   Console::WriteLine("Managed address: {0}", result->address);  
   Console::WriteLine("Managed zip code: {0}", result->zipCode);  
  
   return 0;  
}  
```  
  
 在上述範例中，`marshal_as` 函式會將控制代碼傳回到轉換後的資料。  這麼做是為了要防止建立資料的額外複本。  直接傳回變數會造成與其關聯且不必要的效能成本。  
  
  **Managed name: Jeff Smith**  
**Managed address: 123 Main Street**  
**Managed zip code: 98111**   
## 範例  
 下列範例會將員工資訊從 Managed 資料型別轉換成原生資料型別。  這個轉換需要封送處理內容。  
  
```  
// MyMarshalContext.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr/marshal.h>  
  
value struct ManagedEmp {  
   System::String^ name;  
   System::String^ address;  
   int zipCode;  
};  
  
struct NativeEmp {  
   const char* name;  
   const char* address;  
   int zipCode;  
};  
  
namespace msclr {  
   namespace interop {  
      template<>  
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base  
      {  
      private:  
         NativeEmp* toPtr;  
         marshal_context context;  
      public:  
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)  
         {  
            // Conversion logic starts here  
            toPtr = NULL;  
  
            const char* nativeName;  
            const char* nativeAddress;  
  
            // Convert the name from String^ to const char*.  
            System::String^ tempValue = fromObject->name;  
            nativeName = context.marshal_as<const char*>(tempValue);  
  
            // Convert the address from String^ to const char*.  
            tempValue = fromObject->address;  
            nativeAddress = context.marshal_as<const char*>(tempValue);  
  
            toPtr = new NativeEmp();  
            toPtr->name = nativeName;  
            toPtr->address = nativeAddress;  
            toPtr->zipCode = fromObject->zipCode;  
  
            toObject = toPtr;  
         }  
         ~context_node()  
         {  
            this->!context_node();  
         }  
      protected:  
         !context_node()  
         {  
            // When the context is deleted, it will free the memory  
            // allocated for toPtr->name and toPtr->address, so toPtr  
            // is the only memory that needs to be freed.  
            if (toPtr != NULL) {  
               delete toPtr;  
               toPtr = NULL;  
            }  
         }  
      };  
   }  
}   
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   ManagedEmp^ employee = gcnew ManagedEmp();  
  
   employee->name = gcnew String("Jeff Smith");  
   employee->address = gcnew String("123 Main Street");  
   employee->zipCode = 98111;  
  
   marshal_context context;  
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);  
  
   if (result != NULL) {  
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",  
         result->name, result->address, result->zipCode);  
   }  
  
   return 0;  
}  
```  
  
  **Native name: Jeff Smith**  
**Native address: 123 Main Street**  
**Native zip code: 98111**   
## 請參閱  
 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)