# Welcome!

class Personnage
{
  private $_force;
  private $_localisation;
  private $_experience;
  private $_degats;
        
  // Nous déclarons une méthode dont le seul but est d'afficher un texte.
  public function frapper(Personnage $persoAFrapper)
  {
  	$persoAFrapper->_degats += $this->_force;
  }

   public function gagnerExperience()
  {
  	$this->_experience++;
  }

  public function setForce($force)
  {
  	if (!is_int($force))
  	{
  		trigger_error('la force d\'un personnage doit être un nombre entier', E_USER_WARNING);
  		return;
  	}
  	if ($force > 100)
  	{
  		trigger_error('la force d\'un personnage ne peut dépasser 100', E_USER_WARNING);
  		return;
  	}
  		$this->_force = $force;
  }
  public function setExperience($experience)
  {
  	if (!is_int($experience))
  	{
  		trigger_error('L\experience d\'un personnage doit être un nombre entier', E_USER_WARNING);
  		return;
  	}

  	if ($experience > 100)
  	{
  		trigger_error('L\'experience d\'un personnage ne peut depasser 100', E_USER_WARNING);
  		return;
  	}

  		$this->_experience = $experience;
  }
  	 
  	 public function degats()
  	 {
  	 	return $this->_degats;

  	 }

  	 public function force()
  	 {
  	 	return $this->_force;
  	 }

  	 public function experience()
  	 {
  	 	return $this->_experience;
  	 }
}
    
$perso1 = new Personnage;
$perso2 = new Personnage;

$perso1->setForce(10);
$perso1->setExperience(2);

$perso2->setForce(90);
$perso2->setExperience(58);

$perso1->frapper($perso2);
$perso1->gagnerExperience();

$perso2->frapper($perso1);
$perso2->gagnerExperience();

echo 'le personnage 1 a ', $perso1->force(), ' de force, contrairement au personnage 2 qui a ', $perso2->force(), ' de force.<br />';

echo 'le personnage 1 a ', $perso1->experience(), ' d\'experience, contrairement au personnage 2 qui a ', $perso2->experience(), ' d\'experience.<br />';

echo 'le personnage 1 a ', $perso1->degats(), ' de degats, contrairement au personnage 2 qui a ', $perso2->degats(), ' de degats.<br />';

?>

