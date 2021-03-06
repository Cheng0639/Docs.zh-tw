---
title: 用於 ASP.NET Core SignalR 中樞
author: rachelappel
description: 了解如何使用在 ASP.NET Core SignalR 中樞。
manager: wpickett
ms.author: rachelap
ms.custom: mvc
ms.date: 03/30/2018
ms.prod: aspnet-core
ms.technology: aspnet
ms.topic: article
uid: signalr/hubs
ms.openlocfilehash: 73397ba6951f2752653575920bdf739439874366
ms.sourcegitcommit: 7d02ca5f5ddc2ca3eb0258fdd6996fbf538c129a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="use-hubs-in-signalr-for-aspnet-core"></a>使用 ASP.NET Core 中 SignalR 中樞

由[Rachel Appel](https://twitter.com/rachelappel)和[Kevin Griffin](https://twitter.com/1kevgriff)

## <a name="what-is-a-signalr-hub"></a>SignalR 中樞為何

SignalR 中樞應用程式開發介面可讓您連線的用戶端上呼叫方法，從伺服器。 在伺服器程式碼中，您會定義用戶端所呼叫的方法。 在用戶端程式碼中，您可以定義從伺服器呼叫的方法。 SignalR 會負責在幕後，可讓即時的用戶端-伺服器和伺服器用戶端通訊的所有項目。

## <a name="configure-signalr-hubs"></a>設定 SignalR 中樞

SignalR 的中介軟體需要某些服務，已藉由呼叫`services.AddSignalR`。

[!code-csharp[Configure service](hubs/sample/startup.cs?range=35)]

將 SignalR 功能加入至 ASP.NET Core 應用程式，安裝 SignalR 的路由，藉由呼叫`app.UseSignalR`中`Startup.Configure`方法。

[!code-csharp[Configure routes to hubs](hubs/sample/startup.cs?range=55-58)]

## <a name="create-and-use-hubs"></a>建立和使用集線器

藉由宣告繼承自一個類別建立中樞`Hub`，並將公用方法加入至它。 用戶端可以呼叫方法，定義為`public`。

[!code-csharp[Create and use hubs](hubs/sample/chathub.cs?range=10-13)]

您可以指定傳回型別和參數，包括複雜型別及陣列，您可以按照任何 C# 方法。 SignalR 處理的序列化和還原序列化複雜的物件，並在您的參數和傳回值的陣列。

## <a name="the-clients-object"></a>用戶端物件

每個執行個體`Hub`類別具有內容，名為`Clients`，其中包含伺服器和用戶端之間通訊的下列成員：

| 屬性 | 描述 |
| ------ | ----------- |
| `All` | 所有已連線的用戶端上呼叫的方法 |
| `Caller` | 在用戶端中樞方法叫用呼叫的方法 |
| `Others` | 已叫用方法的用戶端以外的所有連線用戶端上呼叫的方法 |

此外，`Hub`類別包含下列方法：

| 方法 | 描述 |
| ------ | ----------- |
| `AllExcept` | 指定的連接除外的所有已連線用戶端上呼叫的方法 |
| `Client` | 呼叫特定連線的用戶端上的方法 |
| `Clients` | 呼叫特定連線的用戶端上的方法 |
| `Group` | 傳送訊息至指定的群組中的所有連接  |
| `GroupExcept` | 傳送訊息至指定的群組，除了指定的連接中的所有連接 |
| `Groups` | 將訊息傳送至多個連接群組  |
| `OthersInGroup` | 將訊息傳送至的連線，不包括叫用中樞方法的用戶端群組  |
| `User` | 傳送訊息至特定使用者相關聯的所有連接 |
| `Users` | 傳送訊息至指定的使用者相關聯的所有連接 |

每個屬性或方法之前表格中的傳回的物件`SendAsync`方法。 `SendAsync`方法可讓您提供的名稱和用戶端方法呼叫的參數。

## <a name="send-messages-to-clients"></a>將訊息傳送至用戶端

若要讓特定的用戶端呼叫，使用的屬性`Clients`物件。 在下列範例中，下列`SendMessageToCaller`方法將示範將訊息傳送到叫用中樞方法的連線。 `SendMessageToGroups`方法將訊息傳送至儲存在群組`List`名為`groups`。

[!code-csharp[Send messages](hubs/sample/chathub.cs?range=15-24)]

## <a name="handle-events-for-a-connection"></a>處理連接事件

提供 SignalR 中樞 API`OnConnectedAsync`和`OnDisconnectedAsync`用於管理及追蹤連線的虛擬方法。 覆寫`OnConnectedAsync`虛擬方法，當用戶端連線至中樞，例如新增到群組執行動作。

[!code-csharp[Handle events](hubs/sample/chathub.cs?range=26-30)]

## <a name="handle-errors"></a>處理錯誤

在 hub 方法中擲回例外狀況會傳送至已叫用方法的用戶端。 JavaScript 用戶端上`invoke`方法會傳回[JavaScript 承諾](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Using_promises)。 當用戶端會收到錯誤與處理常式附加至承諾使用`catch`，它已叫用，並傳遞為 JavaScript`Error`物件。

[!code-javascript[Error](hubs/sample/chat.js?range=20)]
[!code-javascript[Error](hubs/sample/chat.js?range=16-18)]

## <a name="related-resources"></a>相關資源

[ASP.NET Core SignalR 簡介](xref:signalr/introduction)