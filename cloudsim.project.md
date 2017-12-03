<!-- -. 等于 extends  -->

# hierarchy 类结构图
## brief
CloudLet = 需要完成的任务
Broker = 负责任务的调度和安排
Scheduler = 负责时间的安排
Datacenter = 相当于服务器群，里面有host等资源 (如PE， RAM， BW等)
Host = 相当于服务器，里面有多个VM
Switch = 交换机?
VM = virtual machine 主机里的一个虚拟系统 占用一定的 PE，RAM，BW等
PE = process element 一个运行单位，可以是 1 2 3 ...
RAM = 内存占用 可以是 512MB 1GB 2GB...
BW = bandwidth 占用的宽带
Event = 发送的事件
predicate = 用来比对事件类型？

## CloudLet
ResCloudlet
  ResContainerCloudlet
CloudLet = 立刻要执行的任务
  NetworkCloudlet
  ContainerCloudlet

## SimEntity
SimEntity -> cloneable
  CloudInformationService
  CloudSimShutdown


# simEntity/ Broker
ContainerDatacenterBroker
DatacenterBroker
  PowerDatacenterBroker
NetDatacenterBroker

# simEntity/ Datacenter
Datacenter
  [DatacenterCharacteristics]
  NetworkDatacenter
  PowerDatacenter
    PowerDatacenterNonPowerAware
# simEntity/ Switch 
Switch -> simEntity
  AggregateSwitch
  EdgeSwitch
  RootSwitch

## Host
HostStateHistoryEntry
Host
  HostDynamicWorkload
    PowerHost
      PowerHostUtilizationHistory
  NetworkHost

## VM
VM
  PowerVm
  NetworkVm
VmStateHistoryEntry

## Container
ContainerPe
Container
  PowerContainer
containerCloudSimTags
ContainerDatacenterCharacteristics
ContainerHost
  ContainerHostDynamicWorkload
    PowerContainerHost
      PowerContainerHostUtilizationHistory
ContainerVm
  PowerContainerVm
.
ContainerDatacenter -> simEntity
  PowerContainerDatacenter
    PowerContainerDatacenterCM

## Predicate
Predicate
  PredicateAny
  PredicateFrom
  PredicateNone
  PredicateNotFrom
  PredicateNotType
  PredicateType

## list
CloudletList
HostList
PeList
ResCloudletList
VmList
  PowerVmList
.
ContainerList
ContainerPeList
ContainerHostList
ContainerVmPeList
ContainerVmList
  PowerContainerVmList
PowerContainerList

## PowerModel
-> PowerModel
  PowerModelCubic
  PowerModelLinear
  PowerModelSqrt
  PowerModelSquare
  PowerModelSpecPower
    PowerModelSpecPowerHpProLiantMl110G3PentiumD930
    PowerModelSpecPowerHpProLiantMl110G4Xeon3040
    PowerModelSpecPowerHpProLiantMl110G5Xeon3075
    PowerModelSpecPowerIbmX3250XeonX3470
    PowerModelSpecPowerIbmX3250XeonX3480
    PowerModelSpecPowerIbmX3250XeonX3480
    PowerModelSpecPowerIbmX3550XeonX5675

## Provisioner
BwProvisioner
  BwProvisionerSimple
Preprovisioner
  PeProvisionerSimple
RamProvisioner
  RamProvisionerSimple
.
ContainerBwProvisioner
  ContainerBwProvisionerSimple
ContainerPeProvisioner
  CotainerPeProvisionerSimple
ContainerRamProvisioner
  ContainerRamProvisionerSimple
.
ContainerVmBwProvisioner
  ContainerVmBwProvisionerSimple
ContainerVmPe
ContainerVmPeProvisioner
  ContainerVmPeProvisionerSimple
ContainerVmRamProvisioner
  ContainerVmRamProvisionerSimple

## Scheduler
VmScheduler
  VmSchedulerSpaceShared
  VmSchedulerTimeShared
    VmSchedulerTimeSharedOverSubscription
ContainerScheduler
  ContainerSchedulerTimeShared
    ContainerSchedulerTimeSharedOverSubscription
ContainerVmScheduler
  ContainerVmSchedulerTimeShared
    ContainerVmSchedulerTimeSharedOverSubscription
ContainerCloudletScheduler
  ContainerCloudletSchedulerTimeShared
    ContainerCloudletSchedulerDynamicWorkload
.
CloudletScheduler = 推迟到某个时刻运行的任务
  NetworkCloudletSpaceSharedScheduler
  CloudletSchedulerSpaceShared
  CloudletSchedulerTimeShared
    CloudletSchedulerDynamicWorkload



## Policy
HostSelectionPolicy
  HostSelectionPolicyFirstFit
  HostSelectionPolicyLeastFull
  HostSelectionPolicyMinimumCorrelation
  HostSelectionPolicyMostFull
  HostSelectionPolicyRandomSelection

VmAllocationPolicy
  NetworkVmAllocationPolicy
  VmAllocationPolicySimple
  PowerVmAllocationPolicyAbstract
    PowerVmAllocationPolicyMigrationAbstract
      PowerVmAllocationPolicyMigrationInterQuartileRange
      PowerVmAllocationPolicyMigrationMedianAbsoluteDeviation
      PowerVmAllocationPolicyMigrationStaticThreshold
      PowerVmAllocationPolicyMigrationLocalRegression
        PowerVmAllocationPolicyMigrationLocalRegressionRobust
    PowerVmAllocationPolicySimple

PowerVmSelectionPolicy
  PowerVmSelectionPolicyMaximumCorrelation
  PowerVmSelectionPolicyMinimumMigrationTime
  PowerVmSelectionPolicyMinimumUtilization
  PowerVmSelectionPolicyRandomSelection
PowerContainerSelectionPolicy
  PowerContainerSelectionPolicyCor
  PowerContainerSelectionPolicyMaximumCorrelation
  PowerContainerSelectionPolicyMaximumUsage
  PowerContainerSelectionPolicyMinimumMigrationTime
PowerContainerVmSelectionPolicy
  PowerContainerVMSelectionPolicyCor
  PowerContainerVmSelectionPolicyMaximumCorrelation
  PowerContainerVmSelectionPolicyMaximumUsage
  PowerContainerVmSelectionPolicyMinimumMigrationTime

ContainerPlacementPolicy
  ContainerPlacementPolicyFirstFit
  ContainerPlacementPolicyLeastFull
  ContainerPlacementPolicyMostFull
  ContainerPlacementPolicyRandomSelection
ContainerAllocationPolicy
  ContainerAllocationPolicySimple
  PowerContainerAllocationPolicy
    PowerContainerAllocationPolicySimple
      ContainerAllocationPolicyRS
ContainerVmAllocationPolicy
  ContainerVmAllocationPolicySimple
  PowerContainerVmAllocationAbstract
    PowerContainerVmAllocationSimple
    PowerContainerVmAllocationPolicyMigrationAbstract
      PowerContainerVmAllocationPolicyMigrationStaticThreshold
      PowerContainerVmAllocationPolicyMigrationAbstractHostSelection
      PowerContainerVmAllocationPolicyMigrationAbstractContainerAdded
        PowerContainerVmAllocationPolicyMigrationAbstractContainerHostSelection
          PowerContainerVmAllocationPolicyMigrationStaticThresholdMC
          PowerContainerVmAllocationPolicyMigrationAbstractContainerHostSelectionUnderUtilizedAdded
            PowerContainerVmAllocationPolicyMigrationStaticThresholdMCUnderUtilized


## package/cloudsim
-> UtilizationModel
  UtilizationModelFull
  UtilizationModelNull
  UtilizationModelPlanetLabInMemory
  UtilizationModelStochastic

Object
  Throwable
    Exception
      ParameterException
Object
  Consts
.
  DataCloudTags
  File
  FileAttribute
  HarddriveStorage -> Storage
    SanStorage
  InfoPacket -> Packet
  Log
  NetworkTopology
  Pe = Process element, can be 1 2 3 ...
## package/ container.utils
Object
  Correlation
  CostumeCSVReader
  CostumeCSVWriter
  IDs
  RandomGaussian
  RandomGen
## package/ core
Object
  CloudInformationService
  CloudSimTags
  DeferredQueue
  FutureQueue
  SimEvent
## package/ distributions
-> ContinuousDistribution
  ExponentialDistr
  GammaDistr
  LognormalDistr
  LomaxDistribution
  ParetoDistr
  UniformDistr
  WeibullDistr
  ZipfDistr
## package/ network
Object
  DelayMatrix_Float
  FloydWarshall_Float
  GraphReaderBrite
  GraphReaderIF
  TopologicalGraph
  TopologicalLink
  TopologicalNode
## package/ network.datacenter
Object
  AppCloudlet
    TestBagofTaskApp
    WorkflowApp
  HostPackage
  NetworkConstants
  NetworkPacket
  TaskStage
## package/ util
object
  ExecutionTimeMeasurer
  MathUtil
  WorkloadFileReader -> WorkloadModel


# Environment Introduction
https://www.youtube.com/watch?v=qBFlB5puRRs
[@CIS: cloud informaiton center, take care of registry of datacenter]
[@datacenter [@host [@VM (=virtual machine) Cloudlet1=cl1] [@WM PE(process element, 1 2 3 ...) RAM(like 1GB) BW(bandwidth) Cloudlet2=cl2] ]]
  --> [@CIS]
[@Broker]
  <-{datacenter characteristics}-> [@CIS]
  --> [@datacenter]
[@CloudLets]
  --> [@Broker]


# classes 类
## SimEntity
attribute:
  id
  name
  state
  evbuf = EventBuffer

methods: 
  schedule          发送带数据的event到另一个实体，可以通过 id/port
  scheduleNow       立刻发送信息
  scheduleFirst     发送高优先信息
  scheduleFirstNow  立刻发送高优先信息

  send              发送event到另一个实体
  sendNow           立刻发送
  getNetworkDelay   获取网络延迟，同发送信息得到

  事件相关：
  numEventWaiting   等待事件数量
  selectEvent       选中事件
  cancelEvent       取消事件
  getNextEvent      获取下一个事件
  waitForEvent      等待特定事件
  processEvent      运行事件

  实体相关：
  startEntity       启动实体
  pause             暂停一段时间
  shutdownEntity    关闭实体
  run               运行实体
  clone             复制实体



## datacenter -. SimEntity = 相当于服务器群，里面有host等资源 (如PE， RAM， BW等)
attributes:
  characteristics
  regionalCisName 
  `VmAllocationPolicy`
  lastProcessTime
  `storageList`
  `vmList`
  schedulingInterval

methods 
  registerOtherEntity 子类用来创建为不同资源的
  processEvent 根据不同tag做不同相应 
  processDataDelete 删除文件 
  processDataAdd 添加文件 
  processPingRequest 测ping网络
  processCloudletStatus 返回cloudlet状态
  processOtherEvent 处理其他事件,子类overwrite来处理特别任务 
  processVmCreate 处理创建Vm的Event 
  processVmDestroy 销毁Vm 
  processVmMigrate 迁移Vm 
  processCloudlet 根据事件处理cloudlet 
  processCloudletMove 移动一个cloudlet 
  processCloudletSubmit 运行一个Cloudlet 
  predictFileTransferTime 预计转移文件时间 
  processCloudletResume 恢复运行Cloudlet
  processCloudletPause 暂停运行Cloudlet
  processCloudletCancel 取消Cloudlet 
  updateCloudletProcessing 更新Cloudlet运行资源
  checkCloudletCompletion 查看Cloudlet完成没
  addFile 增加文件到资源 
  contain 检查datacenter包含不包含特定文件
  deleteFileFromStorage 从资源中删除文件 
  shutdownEntity 关闭datacenter
  startEntity 启动datacenter
  getHostList 获取Host列表




## PowerDatacenter -. datacenter =控制能源和迁移
attribute 
  power 消耗的能源
  disableMigrations 是否可迁移
  cloudletSubmitted 最后一次运行 
  migrationCount Vm迁移的次数 
  isInMigration 数据中心是否在迁移

method
  updateCloudletProcessing 更新Cloudlet运行资源
  updateCloudetProcessingWithoutSchedulingFutureEvents 直接更新Cloudlet 
  updateCloudetProcessingWithoutSchedulingFutureEventsForce 强制更新Cloudlet
  processVmMigrate 迁移Vm
  processCloudletSubmit 运行一个Cloudlet 
  incrementMigrationCount 自动1迁移次数

## PowerDatacenterNonPowerAware
attribute 

method 


## Network/ DelayMatrix_Float = 通过delay代表两个node之间的距离 
method 
  calculateShortestPath 计算最短路径 
  createDelayMatrix 创建矩阵存储每个点之间的延迟
  getDelay 获取两个点之间的延迟 
## Network/ FloydWarshall_Float = 


## Network/Datacenter/  NetworkDatacenter -. datacenter = 控制Vm和Switch
attribute 
  VmToSwitchid 匹配Vm和Switch
  HostToSwitchid 匹配Host和Switch 
  Switchlist 匹配交换机和datacenter 
  VmToHostList 匹配Vm和HostList

method
  getEdgeSwitch 获取所有边缘交换机
  processVmCreateNetwork 创建Vm 
  ProcessCloudletSubmit 运行一个Cloudlet