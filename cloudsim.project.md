# hierarchy 类结构图
## brief
CloudLet = 需要完成的任务
Broker = 负责任务的调度和安排
Scheduler = 负责时间的安排
Datacenter = 相当于服务器群，里面有host等资源 (如PE， RAM， BW等)
Host = 相当于服务器，里面有多个VM
VM = virtual machine 主机里的一个虚拟系统 占用一定的 PE，RAM，BW等
PE = process element 一个运行单位，可以是 1 2 3 ...
RAM = 内存占用 可以是 512MB 1GB 2GB...
BW = bandwidth 占用的宽带

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
  ContainerDatacenter
    PowerContainerDatacenter
      PowerContainerDatacenterCM

  ContainerDatacenterBroker
  DatacenterBroker
    PowerDatacenterBroker
  NetDatacenterBroker

  Datacenter
    [DatacenterCharacteristics]
    NetworkDatacenter
    PowerDatacenter
      PowerDatacenterNonPowerAware

  Switch
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
