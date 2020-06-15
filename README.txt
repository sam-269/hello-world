
@Repository
public interface LeavesDao extends JpaRepository<Leaves,Integer> {
    List<Leaves> findByEmpId(Integer id);
}
