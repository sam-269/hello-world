@Component
@Entity
@Table(name="employees")
@JsonIgnoreProperties({"hibernateLazyInitializer", "handler"})
public class Employee implements Serializable {
    private static final long serialVersionUID = 1L;
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name="empid", nullable=false)
    private Integer empId;
    @Column(name="manager", nullable=false)
    private String manager;
    @Column(name="earned_leaves", nullable=false)
    private static Integer earnedLeaves=4;

    @OneToMany(mappedBy = "employee", cascade = CascadeType.ALL, fetch = FetchType.EAGER,targetEntity = Leaves.class)
    private Set<Leaves> leaves;
    public Employee(Integer empId, String manager, Integer earnedLeaves) {
        this.empId = empId;
        this.manager = manager;
        //this.leaves=leaves;
        this.earnedLeaves=earnedLeaves;

    }
    public Employee(){}


    public Integer getEmpId() {
        return empId;
    }
    public void setEmpId(Integer empId) {
        this.empId = empId;
    }
    public String getManager() {
        return manager;
    }
    public void setManager(String manager) {
        this.manager = manager;
    }
    public static Integer getEarnedLeaves() {
        return earnedLeaves;
    }
    public static void setEarnedLeaves(Integer earnedLeaves) {
        Employee.earnedLeaves = earnedLeaves;
    }

    public Set<Leaves> getLeaves() {
        return leaves;
    }

    public void setLeaves(Set<Leaves> leaves) {
        this.leaves = leaves;
    }
}

@Entity
@Table(name="leaves")
@JsonIgnoreProperties({"hibernateLazyInitializer", "handler"})
public class Leaves implements Serializable {
    private static final long serialVersionUID = 1L;
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer leaveid;
    @JsonIgnore
    @Column(name="empid",insertable = false,updatable = false)
    private Integer empId;

    @ManyToOne(fetch = FetchType.EAGER)
    @JoinColumn(name="empid",nullable = false)
    @JsonIgnore
    private Employee employee;

    public Leaves(){};
    public Leaves (Date leaves){
        this.leaves=leaves;
    }
    private Date leaves;

    public Integer getEmpId() {
        return leaveid;
    }

    public void setEmpId(Integer empId) {
        this.leaveid = empId;
    }

    public Date getLeaves() {
        return leaves;
    }

    public void setLeaves(Date leaves) {
        this.leaves = leaves;
    }
}
