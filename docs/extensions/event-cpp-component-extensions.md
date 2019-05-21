---
title: event  (C++/CLI 與 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
ms.openlocfilehash: 26bfc3bb9892486353f55a71cfd86a17f2de98b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516583"
---
# <a name="event--ccli-and-ccx"></a>event  (C++/CLI 與 C++/CX)

**event** 關鍵字會宣告 *事件*，這是對已註冊訂閱者已發生感興趣項目的通知 (*事件處理常式*)。

## <a name="all-runtimes"></a>所有執行階段

C++/CX 支援宣告*事件成員*或*事件區塊*。 事件成員是用來宣告事件區塊的速記。 根據預設，事件成員會宣告事件區塊中明確宣告的 `add()`、`remove()` 和 `raise()` 函式。 若要自訂事件成員中的函式，請改為宣告事件區塊，然後覆寫您所需要的函數。

### <a name="syntax"></a>語法

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>參數

*modifier*<br/>
事件宣告或事件存取子方法上可使用的修飾詞。  可能的值為 **static** 和 **virtual**。

*delegate*<br/>
[委派](delegate-cpp-component-extensions.md)，事件處理常式必須符合其簽章。

*event_name*<br/>
事件的名稱。

*return_value*<br/>
事件存取子方法的傳回值。  若要可供驗證，傳回型別必須是 **void**。

*parameters*<br/>
(選擇性) `raise` 方法的參數，其符合 *delegate* 參數的簽章。

### <a name="remarks"></a>備註

事件是委派與成員函式 (事件處理常式) 之間的關聯，會回應事件的觸發並且允許來自任何類別的用戶端註冊符合基礎委派的簽章和傳回類型的方法。

有兩種類型的事件宣告：

*事件資料成員*<br/>
編譯器會自動以委派類型成員的形式建立事件的儲存體，並建立內部 `add()`、`remove()` 和 `raise()` 成員函式。 事件資料成員必須在類別內宣告。 委派的傳回類型必須符合處理常式的事件的傳回類型。

*事件區塊*<br/>
事件區塊可讓您明確宣告和自訂 `add()`、`remove()` 和 `raise()` 方法的行為。

您可以使用 **operators+=** 與 **operator-=** 來加入和移除事件處理常式，或明確呼叫 `add()` 與 `remove()` 方法。

**event** 是內容相關性關鍵字；如需詳細資訊，請參閱[內容相關性關鍵字](context-sensitive-keywords-cpp-component-extensions.md) \(英文\)。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[事件 (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755799.aspx) \(部分機器翻譯\)。

如果您想要加入然後移除事件處理常式，您必須儲存加入作業所傳回的 EventRegistrationToken 結構。 然後在移除作業中，您必須使用儲存的 EventRegistrationToken 結構來識別要移除的事件處理常式。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

**event** 關鍵字可讓您宣告事件。 事件是類別在發生感興趣的項目時提供通知的方法。

### <a name="syntax"></a>語法

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>參數

*modifier*<br/>
事件宣告或事件存取子方法上可使用的修飾詞。  可能的值為 **static** 和 **virtual**。

*delegate*<br/>
[委派](delegate-cpp-component-extensions.md)，事件處理常式必須符合其簽章。

*event_name*<br/>
事件的名稱。

*return_value*<br/>
事件存取子方法的傳回值。  若要可供驗證，傳回型別必須是 **void**。

*parameters*<br/>
(選擇性) `raise` 方法的參數，其符合 *delegate* 參數的簽章。

### <a name="remarks"></a>備註

事件是委派與成員函式 (事件處理常式) 之間的關聯，會回應事件的觸發並且允許來自任何類別的用戶端註冊符合基礎委派的簽章和傳回類型的方法。

委派可以有一或多個關聯的方法，將在您的程式碼指出事件已發生時呼叫。 一個程式中的事件可供以 .NET Framework Common Language Runtime 為目標的其他程式使用。

有兩種類型的事件宣告：

*事件資料成員*<br/>
以委派類型成員形式的事件儲存體，是由資料成員事件的編譯器建立。  事件資料成員必須在類別內宣告。 這也稱為 trivial 事件 (請參閱以下程式碼範例)。

*事件區塊*<br/>
事件區塊可讓您透過實作 add、remove 和 raise 方法來自訂 add、remove 和 raise 方法的行為。 add、remove 和 raise 方法的簽章必須符合委派的簽章。  事件區塊事件不是資料成員，且用做資料成員的任何使用方式將產生編譯器錯誤。

事件處理常式的傳回類型必須符合委派的傳回類型。

在 .NET Framework 中，您可以將資料成員視同方法本身 (也就是，其對應委派的 `Invoke` 方法)。 您必須預先定義用來宣告 Managed 事件資料成員的委派類型。 相反地，Managed 事件方法會隱含定義對應的 Managed 委派 (如果尚未定義的話)。  如需範例，請參閱本主題結尾處的程式碼範例。

宣告 Managed 事件時，您可以指定事件處理常式是使用運算子 += 和 -= 呼叫時，將呼叫的加入和移除存取子。 可以明確呼叫 add、remove 和 raise 方法。

若要在 Visual C++ 中建立及使用事件，必須採取下列步驟：

1. 建立或識別委派。 如果要定義自己的事件，您也必須確定有委派以與 **event** 關鍵字搭配使用。 如果已預先定義事件 (例如在 .NET Framework 中)，則事件的取用者只需要知道委派的名稱。

2. 建立包含下列的類別：

   - 從委派建立的事件。

   - (選擇性) 方法，驗證使用 **event** 關鍵字宣告的委派的執行個體存在。 否則，此邏輯必須放置在引發事件的程式碼中。

   - 呼叫此事件的方法。 這些方法可以是某些基底類別功能的覆寫。

   這個類別會定義事件。

3. 定義將方法連接到事件的一或多個類別。 每個類別會將一個或多個方法與基底類別中的事件建立關聯。

4. 使用事件：

   - 建立物件的類別，其中包含事件宣告。

   - 建立物件的類別，其中包含事件定義。

如需 C++/CLI 事件的詳細資訊，請參閱

- [介面中的事件](../dotnet/how-to-use-events-in-cpp-cli.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列程式碼範例會示範宣告成對的委派、事件和事件處理常式；訂閱 (加入) 事件處理常式；叫用事件處理常式；然後取消訂閱 (移除) 事件處理常式。

```cpp
// mcppv2_events.cpp
// compile with: /clr
using namespace System;

// declare delegates
delegate void ClickEventHandler(int, double);
delegate void DblClickEventHandler(String^);

// class that defines events
ref class EventSource {
public:
   event ClickEventHandler^ OnClick;   // declare the event OnClick
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick

   void FireEvents() {
      // raises events
      OnClick(7, 3.14159);
      OnDblClick("Hello");
   }
};

// class that defines methods that will called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }

   void OnMyDblClick(String^ str) {
      Console::WriteLine("OnDblClick: {0}", str);
   }
};

int main() {
   EventSource ^ MyEventSource = gcnew EventSource();
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);

   // invoke events
   MyEventSource->FireEvents();

   // unhook handler to event
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);
}
```

```Output
OnClick: 7, 3.14159

OnDblClick: Hello
```

下列程式碼範例示範用於產生簡單事件之 `raise` 方法的邏輯：若事件有一或多個訂閱者，以隱含或明確方式呼叫 `raise` 方法會呼叫委派。 如果委派的傳回型別不是 **void**，而且如果有零個事件訂閱者，`raise` 方法會傳回委派類型的預設值。 如果沒有任何事件訂閱者，呼叫 `raise` 方法只會傳回，而且不會引發任何例外狀況。 如果委派傳回型別不是 **void**，則會傳回委派類型。

```cpp
// trivial_events.cpp
// compile with: /clr /c
using namespace System;
public delegate int Del();
public ref struct C {
   int i;
   event Del^ MyEvent;

   void FireEvent() {
      i = MyEvent();
   }
};

ref struct EventReceiver {
   int OnMyClick() { return 0; }
};

int main() {
   C c;
   c.i = 687;

   c.FireEvent();
   Console::WriteLine(c.i);
   c.i = 688;

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);
   Console::WriteLine(c.i);
}
```

```Output
0

688
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)