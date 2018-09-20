---
title: 如何： 擴充封送處理程式庫 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4e50ca6fd99f373a65ba0592114cb7d9eedb242
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384900"
---
# <a name="how-to-extend-the-marshaling-library"></a>如何：擴充封送處理程式庫

本主題說明如何擴充封送處理程式庫，以提供更多資料型別之間的轉換。 使用者可以擴充程式庫目前不支援任何資料轉換的封送處理程式庫。

您可以擴充封送處理程式庫中有兩種-包含或不含[marshal_context 類別](../dotnet/marshal-context-class.md)。 檢閱[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)主題，以判斷新的轉換是否需要內容。

在這兩種情況下，您可以先建立新的封送處理轉換的檔案。 這麼一來保留標準的封送處理程式庫檔案的完整性。 如果您想要移植至另一部電腦或另一個程式的專案，您必須複製新的封送處理檔案和其餘的專案。 如此一來，在收到專案的使用者保證收到新的轉換，並不會修改任何程式庫檔案。

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>若要擴充的轉換不需要內容來封送處理程式庫

1. 建立檔案以儲存新的封送處理函數，例如 MyMarshal.h。

1. 包含一或多個封送處理程式庫檔案：

   - marshal.h 針對基底類型。

   - marshal_windows.h windows 資料類型。

   - marshal_cppstd.h c + + 標準程式庫的資料類型。

   - marshal_atl.h ATL 資料類型。

1. 使用這些步驟的結尾的程式碼撰寫的轉換函式。 在此程式碼中，若要將轉換成的型別，FROM 的類型轉換，和`from`是要轉換的參數。

1. 以要轉換的程式碼取代有關轉換邏輯的註解`from`參數插入到的物件類型，並傳回已轉換的物件。

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>若要擴充的轉換需要內容來封送處理程式庫

1. 建立檔案以儲存新的封送處理函數，例如 MyMarshal.h

1. 包含一或多個封送處理程式庫檔案：

   - marshal.h 針對基底類型。

   - marshal_windows.h windows 資料類型。

   - marshal_cppstd.h c + + 標準程式庫的資料類型。

   - marshal_atl.h ATL 資料類型。

1. 使用這些步驟的結尾的程式碼撰寫的轉換函式。 在此程式碼中，若要將轉換成的型別，FROM 的類型轉換，`toObject`是用來儲存結果、 指標和`fromObject`是要轉換的參數。

1. 關於初始化程式碼，以初始化註解取代`toPtr`適當的空值。 例如，如果它是指標，將它設定為`NULL`。

1. 以要轉換的程式碼取代有關轉換邏輯的註解`from`參數的物件插入*TO*型別。 此轉換的物件會儲存在`toPtr`。

1. 取代設定的相關註解`toObject`程式碼，以設定`toObject`已轉換的物件。

1. 清除程式碼，以釋放所配置任何記憶體的原生資源的相關註解取代`toPtr`。 如果`toPtr`使用配置的記憶體`new`，使用`delete`釋放的記憶體。

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

下列範例會擴充封送處理程式庫，不需要內容的轉換。 在此範例中，程式碼會將員工資訊至 managed 的資料類型轉換從原生資料型別。

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

在上述範例中，`marshal_as`函式傳回的控制代碼轉換的資料。 這麼做是為了防止建立另一份資料。 直接傳回變數會有不必要的效能成本與其相關聯。

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>範例

下列範例會轉換成原生資料類型從受管理的資料類型的員工資訊。 這個轉換所需的封送處理的內容。

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

## <a name="see-also"></a>另請參閱

[C++ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)