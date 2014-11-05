
## Example

### grid builder class
```
class GridBuilder  extends \JO\Nette\Doctrine\EntityGridoManager
{
/**
 *
 * @return Grid
 */
public function registerColumns()
{
    $this->dg->model = $this->em->getRepository($this->entity)->getGridDataSource();

    $this->addCols(['name','slug','description'],true,true);

    $this->dg->setFilterRenderType(Filter::RENDER_INNER);


    return $this->dg;
}
}
```

### presenter
```
protected function createComponentProductGroupGrid($name)
{
    $this->gridBuilder = new GridBuilder('entityClassName', $entityManager, new \Grido\Grid($this, $name)$this->translator);
    return $this->gridBuilder->registerColumns();
}
```