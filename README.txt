@Service

public class LeaveService {
    @Autowired
    private LeavesDao leavesDao;

    public List<Leaves> getLeavesById(Integer id) {
        if (!leavesDao.existsById(id)) {
            throw new NotFoundException("Employee not found");
        }
        return leavesDao.findByEmpId(id);
    }

    public List<Date> method1(Integer id) {
        List<Leaves> temp=leavesDao.findByEmpId(id);
        List<Date> all_leaves=new ArrayList<Date>();
        for (int i = 0; i < temp.size(); i++){
            all_leaves.add(temp.get(i).getLeaves());
        }
        return all_leaves;
    }


    public List<Date> checkLeaves(Integer id, Date startDate, Date endDate) {
        if(startDate== null || endDate== null){
            throw new ApiRequestException("Dates cannot be null");
        }
        if (startDate.after(endDate)){
            throw new ApiRequestException("End date cannot be before start date");
        }
        List<Date> all_leaves=method1(id);
        List<Date> list = new ArrayList<Date>();
        for(int i=0; i<all_leaves.size(); i++){
            if(startDate.before(all_leaves.get(i))){
                if(endDate.after(all_leaves.get(i))){
                    list.add(all_leaves.get(i));
                }
            }
        }
        //return this.employee.get(empId).getLeaves();
        return list;
    }

    public Integer applyLeaves(Integer id,Date fromDate, Date toDate) {
        return 1;
    }
}
