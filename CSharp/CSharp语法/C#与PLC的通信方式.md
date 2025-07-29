C#与PLC的通信方式

### 1. 串口通信（RS232/RS485）
适用于老式PLC或工业设备
```csharp
using System.IO.Ports;

SerialPort sp = new SerialPort("COM1", 9600, Parity.None, 8, StopBits.One);
sp.Open();
sp.Write("READ_REGISTER\n");  // 发送自定义协议指令
string response = sp.ReadExisting();  // 接收响应数据
```

### 2. Modbus TCP协议
工业标准协议，支持以太网通信
```csharp
// 使用NModbus库示例
var adapter = new TcpClientAdapter("192.168.0.1", 502);
var factory = new DefaultModbusMessageFactory();
var request = factory.CreateReadHoldingRegistersRequest(1, 0, 10); // 从站ID=1，地址0读取10个寄存器
var response = adapter.Send<ReadHoldingRegistersResponse>(request);
```

### 3. S7协议（西门子PLC专用）
使用S7.NET库实现西门子PLC通信
```csharp
using S7.Net;

Plc plc = new Plc(CpuType.S71200, "192.168.0.1", 0, 1);
plc.Open();
var db = plc.DBRead(1, 0, 10); // 读取DB1的10字节数据
plc.Close();
```

### 4. OPC UA协议（工业标准）
适用于复杂工业场景
```csharp
// 使用OPC Foundation SDK
var endpoint = new Uri("opc.tcp://192.168.0.1:4840");
var channel = new TcpClientChannel(endpoint);
var session = Session.Create(channel);
var node = session.ReadNode("ns=3;s=|var|CODESYS Control Win V3 x64.Application.PLC_PRG.Value");
```

### 注意事项：
1. 需根据PLC型号选择对应协议
2. 网络通信需配置正确的IP和端口
3. 数据类型转换需注意字节序（BitConverter.IsLittleEndian）
4. 建议添加超时和重试机制
5. 使用专用库时需注意许可证协议

推荐优先使用Modbus TCP或OPC UA等标准协议，每家公司的协议都有不同，很多协议是公司自己 定义的，具体传输协议需参考PLC厂商的通信规范文档。