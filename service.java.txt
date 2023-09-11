package details.com.example.detailsservice.demo.serviceimpl;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import details.com.example.detailsservice.demo.Exception.BussinessException;
import details.com.example.detailsservice.demo.Repository.DetailsRepo;
import details.com.example.detailsservice.demo.Service.DetailsService;
import details.com.example.detailsservice.demo.entity.Details;
@Service
public class Detailsserviceimpl implements DetailsService {
	@Autowired
	private DetailsRepo repo;

	@Override
	public Details saveDetails(Details details) {
		return repo.save(details);
	}
		


	@Override
	public List<Details> getAllDetails() {
		return repo.findAll();
	}

	@Override
	public Details getByDetailsId(long id) {
		return repo.findById(id).get();
	}

	@Override
	public Details updateByDetailsId(long id, Details details) {
		Details det = repo.findById(id).get();
	    det.setCost(details.getCost());
	    det.setRam(details.getRam());
	    det.setStorage(details.getStorage());
	    det=repo.save(det);
	    return det;
	}

	@Override
	public Details DeleteByDetailsId(long id) {
	     Details det = repo.findById(id).get();
	     if(det!=null) {
	    	 repo.delete(det);
	     }
	     else {
	    	 
	     }
	     return null;
	      }
		
	}


