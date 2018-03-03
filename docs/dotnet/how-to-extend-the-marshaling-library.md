---
title: "如何： 擴充封送處理程式庫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ee919e1faa37959d25e8e42581c8cde80d640337
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-extend-the-marshaling-library"></a>如何：擴充封送處理程式庫
本主題說明如何擴充封送處理程式庫提供更多資料類型之間轉換。 使用者可以擴充封送處理程式庫目前不支援任何資料轉換。  
  
 您可以擴充封送處理程式庫中有兩種-含[marshal_context 類別](../dotnet/marshal-context-class.md)。 檢閱[概觀的封送處理 c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)主題，以判斷新的轉換是否需要內容。  
  
 在這兩種情況下，您可以先建立新的封送處理轉換的檔案。 您要保留標準封送處理程式庫檔案的完整性。 如果您想要移植到其他電腦或另一個程式設計人員的專案，您必須複製新的封送處理檔案，以及專案其餘部分。 這種方式，使用者會接收專案保證收到新的轉換，並不會修改任何程式庫檔案。  
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>若要擴充封送處理程式庫不需要內容的轉換  
  
1.  建立檔案以儲存新的封送處理功能，例如 MyMarshal.h。  
  
2.  包含一或多個封送處理程式庫檔案：  
  
    -   marshal.h 基底類型。  
  
    -   marshal_windows.h windows 資料類型。  
  
    -   c + + 標準程式庫的資料類型的 marshal_cppstd.h。  
  
    -   marshal_atl.h ATL 資料類型。  
  
3.  使用結尾的步驟執行的程式碼，來撰寫轉換函式。 在此程式碼，將轉換成類型、 FROM 為類型轉換，和`from`是要轉換的參數。  
  
4.  要轉換的程式碼以取代註解轉換邏輯`from`若要為物件的參數類型與傳回已轉換的物件。  
  
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
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>若要擴充封送處理程式庫需要內容的轉換  
  
1.  建立檔案以儲存新的封送處理功能，例如 MyMarshal.h  
  
2.  包含一或多個封送處理程式庫檔案：  
  
    -   marshal.h 基底類型。  
  
    -   marshal_windows.h windows 資料類型。  
  
    -   c + + 標準程式庫的資料類型的 marshal_cppstd.h。  
  
    -   marshal_atl.h ATL 資料類型。  
  
3.  使用結尾的步驟執行的程式碼，來撰寫轉換函式。 在此程式碼，將轉換成類型、 FROM 為類型轉換，`toObject`是用來儲存結果，指標和`fromObject`是要轉換的參數。  
  
4.  取代註解程式碼，以初始化初始化`toPtr`適當的空值。 例如，如果是指標，將它設定為`NULL`。  
  
5.  要轉換的程式碼以取代註解轉換邏輯`from`參數的物件插入*TO*型別。 此轉換的物件會儲存在`toPtr`。  
  
6.  設定的相關註解取代`toObject`與程式碼以設定`toObject`要轉換的物件。  
  
7.  清除程式碼，以釋放所配置任何記憶體的原生資源的相關註解取代`toPtr`。 如果`toPtr`配置的記憶體使用`new`，使用`delete`釋放的記憶體。  
  
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
  
## <a name="example"></a>範例  
 下列範例將擴充封送處理不需要內容的轉換。 在此範例中，程式碼將 「 員工 」 資訊從原生資料類型的 managed 的資料類型。  
  
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
  
 在上述範例中，`marshal_as`函式傳回的控制代碼轉換的資料。 這是為了避免建立額外的資料副本。 直接傳回變數會具有不必要的效能成本與其關聯。  
  
```Output  
Managed name: Jeff Smith  
Managed address: 123 Main Street  
Managed zip code: 98111  
```  
  
## <a name="example"></a>範例  
 下列範例會將 「 員工 」 資訊從受管理的資料類型轉換成原生資料類型。 此轉換需要封送處理內容。  
  
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
  
```Output  
Native name: Jeff Smith  
Native address: 123 Main Street  
Native zip code: 98111  
```  
  
## <a name="see-also"></a>請參閱  
 [C++ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)