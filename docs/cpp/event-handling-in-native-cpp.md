---
title: 原生 C++ 中的事件處理
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: cc9265cd3f9f400e2880405019e4d2c9a934f10a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180078"
---
# <a name="event-handling-in-native-c"></a>原生 C++ 中的事件處理

在原C++生事件處理中，您會分別使用[event_source](../windows/attributes/event-source.md)和[event_receiver](../windows/attributes/event-receiver.md)屬性來設定事件來源和事件接收器，以指定 `type`=`native`。 這些屬性可讓套用它們的類別引發事件，以及在原生的非 COM 內容中處理事件。

## <a name="declaring-events"></a>宣告事件

在事件來源類別中，請在方法宣告上使用[__event](../cpp/event.md)關鍵字，將方法宣告為事件。 請務必宣告方法，但不要定義方法；這樣會產生編譯器錯誤，因為編譯器會在將方法變成事件時隱含定義該方法。 原生事件可以是包含零個或多個參數的方法。 傳回型別可為 void 或任何整數類型。

## <a name="defining-event-handlers"></a>定義事件處理常式

在事件接收器類別中，您會定義事件處理常式，其為具有簽章 (傳回類型、呼叫慣例和引數)，符合將處理之事件的方法。

## <a name="hooking-event-handlers-to-events"></a>攔截事件的事件處理常式

此外，在事件接收器類別中，您可以使用內建函式[__hook](../cpp/hook.md)來建立事件與事件處理常式之間的關聯，以及從事件處理常式[__unhook](../cpp/unhook.md)至中斷關聯事件。 您可以在事件處理常式中攔截多個事件，或在事件中攔截多個事件處理常式。

## <a name="firing-events"></a>引發事件

若要引發事件，只要呼叫在事件來源類別中宣告為事件的方法即可。 如果在事件中攔截到處理常式，則會呼叫處理常式。

### <a name="native-c-event-code"></a>原生 C++ 事件代碼

下列範例示範如何在原生 C++ 中引發事件。 若要編譯和執行這個範例，請參閱程式碼中的註解。

## <a name="example"></a>範例

### <a name="code"></a>程式碼

```cpp
// evh_native.cpp
#include <stdio.h>

[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};

[event_receiver(native)]
class CReceiver {
public:
   void MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
   }

   void MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
   }

   void hookEvent(CSource* pSource) {
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void unhookEvent(CSource* pSource) {
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   CSource source;
   CReceiver receiver;

   receiver.hookEvent(&source);
   __raise source.MyEvent(123);
   receiver.unhookEvent(&source);
}
```

### <a name="output"></a>輸出

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>另請參閱

[事件處理](../cpp/event-handling.md)
