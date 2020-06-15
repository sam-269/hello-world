# hello-world
First repository ever
@RestController
@RequestMapping("/api")

public class LeaveController {
    @Autowired
    private LeaveService leaveService;

//    @HystrixCommand(fallbackMethod = "runLeaveFallback", commandProperties = {
//    @HystrixProperty(name = "circuitBreaker.requestVolumeThreshold", value =
//                    "100"),
//    @HystrixProperty(name = "circuitBreaker.errorThresholdPercentage", value =
//                    "20"),
//
//    @HystrixProperty(name = "circuitBreaker.sleepWindowInMilliseconds", value =
//                    "1000"),
//    @HystrixProperty(name = "execution.isolation.thread.timeoutInMilliseconds",
//                    value = "10000") })

    @GetMapping("/{id}")
    public List<Leaves> getLeavesById(@PathVariable("id") Integer id){

        return leaveService.getLeavesById(id);
    }

    @GetMapping("all_leaves/{id}")
    public List<Date> method1(@PathVariable("id") Integer id)
    {
        return leaveService.method1(id);
    }

    @PostMapping("leaves/{id}")
    public List<Date> checkLeaves(@PathVariable("id") Integer id,
                                  @NotNull @RequestBody DateParams date) {
    	return leaveService.checkLeaves(id,date.getStartdate(),date.getEnddate());
    }


    @PostMapping("leaves2/{id}")
    public Integer applyLeaves( @PathVariable("id")Integer id,
                                @RequestBody DateParams date){
        return leaveService.applyLeaves(id,date.getFromDate(),date.getToDate());
    }

    public String runLeaveFallback(){
        return "Some Error occurred on the server, try again";
    }

    @GetMapping("jsp")
    public ModelAndView hello(Model model) {
        ModelAndView mav = new ModelAndView();
        mav.setViewName("index");
        return mav;
    }
   
