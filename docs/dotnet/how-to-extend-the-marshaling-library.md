---
title: 如何：擴充封送處理程式庫
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: 2a3dccd33b7ad2caee64e31e0f79180dda4649be
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216384"
---
# <a name="how-to-extend-the-marshaling-library"></a>如何：擴充封送處理程式庫

本主題說明如何擴充封送處理程式庫，以提供資料類型之間的更多轉換。 使用者可以針對程式庫目前不支援的任何資料轉換擴充封送處理程式庫。

您可以使用兩種方式之一擴充封送處理程式庫-不論是否有[Marshal_coNtext 類別](../dotnet/marshal-context-class.md)。 請參閱[c + + 中的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)主題，以判斷新轉換是否需要內容。

在這兩種情況下，您會先建立檔案以進行新的封送處理轉換。 若要保留標準封送處理程式庫檔案的完整性，請這麼做。 如果您想要將專案移植到另一部電腦或另一位程式設計人員，您必須將新的封送處理檔案連同專案的其餘部分一起複製。 如此一來，接收專案的使用者將保證會收到新的轉換，而且不需要修改任何程式庫檔案。

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>若要使用不需要內容的轉換來擴充封送處理程式庫

1. 建立檔案來儲存新的封送處理函數，例如 MyMarshal。

1. 包含一個或多個封送處理程式庫檔案：

   - 基底類型的封送處理. h。

   - 適用于 windows 資料類型的 marshal_windows .h。

   - c + + 標準程式庫資料類型 marshal_cppstd .h。

   - 適用于 ATL 資料類型的 marshal_atl .h。

1. 在這些步驟的結尾使用程式碼，以撰寫轉換函式。 在此程式碼中，TO 是要轉換成的型別，FROM 是要轉換的來源型別，而 `from` 是要轉換的參數。

1. 將轉換邏輯的批註取代為程式碼，以將 `from` 參數轉換成的物件，以輸入並傳回轉換的物件。

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>若要使用需要內容的轉換來擴充封送處理程式庫

1. 建立檔案來儲存新的封送處理函數，例如 MyMarshal。

1. 包含一個或多個封送處理程式庫檔案：

   - 基底類型的封送處理. h。

   - 適用于 windows 資料類型的 marshal_windows .h。

   - c + + 標準程式庫資料類型 marshal_cppstd .h。

   - 適用于 ATL 資料類型的 marshal_atl .h。

1. 在這些步驟的結尾使用程式碼，以撰寫轉換函式。 在此程式碼中，TO 是要轉換成的型別，FROM 是要從中轉換的型別， `toObject` 是要在其中儲存結果的指標，而 `fromObject` 是要轉換的參數。

1. 將初始化時的批註取代為程式碼，以將初始化 `toPtr` 為適當的空白值。 例如，如果它是指標，請將它設定為 `NULL` 。

1. 以程式碼取代轉換邏輯的批註，將 `from` 參數轉換成的物件 *，以*輸入。 這個轉換的物件將會儲存在中 `toPtr` 。

1. 將 [關於設定的批註] 取代為 [ `toObject` 程式碼]，設定為 `toObject` 轉換的物件。

1. 以程式碼取代清除原生資源的相關批註，以釋放所配置的任何記憶體 `toPtr` 。 如果 `toPtr` 使用配置記憶體 **`new`** ，請使用 **`delete`** 來釋放記憶體。

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

下列範例會使用不需要內容的轉換來擴充封送處理程式庫。 在此範例中，程式碼會將員工資訊從原生資料類型轉換成 managed 資料類型。

```cpp
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

在上述範例中，函式會傳回已 `marshal_as` 轉換資料的控制碼。 這麼做是為了防止建立額外的資料複本。 直接傳回變數會有與其相關聯的不必要效能成本。

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>範例

下列範例會將員工資訊從 managed 資料類型轉換成原生資料類型。 這種轉換需要封送處理內容。

```cpp
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

[C + + 中的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)
