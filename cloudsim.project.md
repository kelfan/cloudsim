# hierarchy 类结构图




## package/
Object
## package/
Object
## package/
Object
## package/
Object
## package/
Object
## package/
Object
## package/
Object
## package/container.resourceAllocatorMigrationEnabled
Object

## package/container.resourceAllocators
Object
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

## package/ container.schedulaers
Object
  ContainerCloudletScheduler
    ContainerCloudletSchedulerTimeShared
      ContainerCloudletSchedulerDynamicWorkload
  ContainerScheduler
    ContainerSchedulerTimeShared
      ContainerSchedulerTimeSharedOverSubscription
  ContainerVmScheduler
    ContainerVmSchedulerTimeShared
      ContainerVmSchedulerTimeSharedOverSubscription

## package/ container.utils
Object
  Correlation
  CostumeCSVReader
  CostumeCSVWriter
  IDs
  RandomGaussian
  RandomGen

## package/ container.core
Object
  PowerContainerVmSelectionPolicy
    PowerContainerVMSelectionPolicyCor
    PowerContainerVmSelectionPolicyMaximumCorrelation
    PowerContainerVmSelectionPolicyMaximumUsage
    PowerContainerVmSelectionPolicyMinimumMigrationTime

## package/ core
--> package/ power/ SimEntity
Object
  CloudInformationService
  CloudSimTags
  DeferredQueue
  FutureQueue
  SimEvent




## package/ predicates
Object
  Predicate
    PredicateAny
    PredicateFrom
    PredicateNone
    PredicateNotFrom
    PredicateNotType
    PredicateType

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

## package/ list
Object
  CloudletList
  HostList
  PeList
  ResCloudletList
  VmList
    PowerVmList
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
--> package/ power/ Switch
--> package/ power/ Host
--> package/ power/ Vm
--> package/ power/ VmAllocationPolicy
Object
  CloudLet = 立刻要执行的任务
    NetworkCloudlet
  AppCloudlet
    TestBagofTaskApp
    WorkflowApp
  CloudletScheduler = 推迟到某个时刻运行的任务
    NetworkCloudletSpaceSharedScheduler
  HostPackage
  NetworkConstants
  NetworkPacket
  TaskStage

## package/ power
Object
  SimEntity -> cloneable
    CloudInformationService
    CloudSimShutdown
    ContainerDatacenter
      PowerContainerDatacenter
        PowerContainerDatacenterCM
    ContainerDatacenterBroker
    Datacenter
      NetworkDatacenter
      PowerDatacenter
        PowerDatacenterNonPowerAware
    DatacenterBroker
      PowerDatacenterBroker
    NetDatacenterBroker
    Switch
      AggregateSwitch
      EdgeSwitch
      RootSwitch
  Host
    HostDynamicWorkload
      PowerHost
        PowerHostUtilizationHistory
    NetworkHost
  VM
    PowerVm
    NetworkVm
  VmAllocationPolicy
    PowerVmAllocationPolicyAbstract
      PowerVmAllocationPolicyMigrationAbstract
        PowerVmAllocationPolicyMigrationInterQuartileRange
        PowerVmAllocationPolicyMigrationMedianAbsoluteDeviation
        PowerVmAllocationPolicyMigrationStaticThreshold
        PowerVmAllocationPolicyMigrationLocalRegression
          PowerVmAllocationPolicyMigrationLocalRegressionRobust
      PowerVmAllocationPolicySimple
      NetworkVmAllocationPolicy
  PowerVmSelectionPolicy
    PowerVmSelectionPolicyMaximumCorrelation
    PowerVmSelectionPolicyMinimumMigrationTime
    PowerVmSelectionPolicyMinimumUtilization
    PowerVmSelectionPolicyRandomSelection


## package/ power.lists
Object
  VimList
    PowerVmList

## package/ power.models
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

## package/ provisioners
Object
  BwProvisioner
    BwProvisionerSimple
  Preprovisioner
    PeProvisionerSimple
  RamProvisioner
    RamProvisionerSimple
## package/ util
object
  ExecutionTimeMeasurer
  MathUtil
  WorkloadFileReader -> WorkloadModel
